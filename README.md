1. 部署 gocd 

   `docker-compose run -d gocd-agent-dind1`

2. 自动 enable agent

   需要在 docker-compose.yaml gocd agent 中指定 `AGENT_AUTO_REGISTER_KEY` 环境变量，`AGENT_AUTO_REGISTER_KEY` 值可以在 `config/cruise-config.xml` 文件中 `agentAutoRegisterKey` 找到

3. 默认用户账号密码

   需要在`config/cruise-config.xml`文件中 admin 元素，下添加 user 元素，每一个 user 都是一个默认账户

   密码在`config/password.properties`格式为：

   `admin={password}` The plugin currently supports passwords hashed using `bcrypt`, `PBKDF2` and `SHA1`. See [#13](https://github.com/gocd/gocd-filebased-authentication-plugin/issues/13) for details. generate password command: `python3 -c "import sha; from base64 import b64encode; print b64encode(sha.new('my-password').digest())"`

   文档：https://github.com/gocd/gocd-filebased-authentication-plugin

