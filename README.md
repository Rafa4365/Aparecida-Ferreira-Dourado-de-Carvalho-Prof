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
