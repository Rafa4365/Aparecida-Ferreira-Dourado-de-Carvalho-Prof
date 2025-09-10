# Aparecida-Ferreira-Dourado-de-Carvalho-Prof

</head>
<body>
    <form id="form1" runat="server">
        <div class="container">
            <h1>Cadastro de Usuário</h1>
            <div>
                <label for="txtNome">Nome:</label>
                <input type="text" id="txtNome" runat="server" />
            </div>
            <div>
                <label for="txtEmail">E-mail:</label>
                <input type="email" id="txtEmail" runat="server" />
            </div>
            <div>
                <label for="txtSenha">Senha:</label>
                <input type="password" id="txtSenha" runat="server" />
            </div>
            <button id="btnCadastrar" runat="server" onserverclick="btnCadastrar_Click">Cadastrar</button>
            <div id="mensagem" runat="server"></div>
        </div>
    </form>
</body>
</html>

<configuration>
  <connectionStrings>
    <add name="ConexaoDB"
         connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=ProjetoWebDB;Integrated Security=True"
         providerName="System.Data.SqlClient" />
  </connectionStrings>
  <system.web>
    <compilation debug="true" targetFramework="4.8"/>
    <pages controlRenderingCompatibilityVersion="4.0"/>
  </system.web>
</configuration>

using System;
using System.Data.SqlClient;
using System.Web.UI;

public partial class _Default : Page
{
    protected void btnCadastrar_Click(object sender, EventArgs e)
    {
        string nome = txtNome.Value;
        string email = txtEmail.Value;
        string senha = txtSenha.Value;

        string connectionString = System.Configuration.ConfigurationManager.ConnectionStrings["ConexaoDB"].ConnectionString;

        try
        {
            using (SqlConnection conn = new SqlConnection(connectionString))
            {
                string query = "INSERT INTO Usuarios (Nome, Email, Senha) VALUES (@Nome, @Email, @Senha)";
                SqlCommand cmd = new SqlCommand(query, conn);
                cmd.Parameters.AddWithValue("@Nome", nome);
                cmd.Parameters.AddWithValue("@Email", email);
                cmd.Parameters.AddWithValue("@Senha", senha); // OBS: Não armazene senhas em texto puro!

                conn.Open();
                cmd.ExecuteNonQuery();
                mensagem.InnerHtml = "<span style='color:green;'>Usuário cadastrado com sucesso!</span>";
            }
        }
        catch (Exception ex)
        {
            mensagem.InnerHtml = $"<span style='color:red;'>Erro ao cadastrar: {ex.Message}</span>";
        }
    }
}
CREATE TABLE Usuarios (
    Id INT IDENTITY PRIMARY KEY,
    Nome NVARCHAR(100),
    Email NVARCHAR(100),
    Senha NVARCHAR(255)
);

