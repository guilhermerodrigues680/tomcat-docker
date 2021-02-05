# TOMCAT no Docker

## Orientações

### Ativando e Acessando os **Default web applications** do Tomcat

No arquivo `docker-compose.yml` você pode escolher montar o volume webapps ou webapps.dist

A diferença é que o volume `./webapps.dist:/usr/local/tomcat/webapps` possui os aplicativos padrões do tomcat, equanto o volume `./webapps:/usr/local/tomcat/webapps` não possui nenhuma aplicação.

Nos arquivos abaixo foi adicionada `allow=".*"` para permitir o acesso dos aplicativos padrão do tomcat a partir de qualquer origem.

- `./webapps.dist/host-manager/META-INF/context.xml`
- `./webapps.dist/host-manager/WEB-INF/manager.xml`
- `./webapps.dist/manager/META-INF/context.xml`

### Credencias

O arquivo local `./conf/tomcat-users.xml` foi montado dentro do container do tomcat.

Assim, a credencial de administrador configurada nesse arquivo foi:

- **username**: admin
- **password**: toor
- **roles**:
    - tomcat,
    - role1,
    - admin,
    - admin-gui,
    - admin-script,
    - manager,
    - manager-gui

### Logs

A pasta local `./logs` foi montada dentro do container do tomcat, assim todos os logs gerados estão disponeis nela.
