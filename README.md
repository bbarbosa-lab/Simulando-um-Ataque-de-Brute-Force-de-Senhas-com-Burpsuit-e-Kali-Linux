# Simulando-um-Ataque-de-Brute-Force-de-Senhas-com-Burpsuit-e-Kali-Linux #
O presente trabalho refere-se ao trabalho prático "Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux"

Como o enunciado do trabalho descreveu que o aluno poderia experimentar com outras ferramentas, o trabalho foi apresentado com algumas alterações:
Primeiramente não será usado o Medusa, também não será usado uma porta FTP, mas sim um http. Será usado o software gráfico Burpsuite, em conjunto com a plataforma de testes do Damn Vulnerable Web Application, sendo um ataque de brute force onde será possível descobrir as credenciais de acesso do administrador, login e senha.

Atenção: Este desafio é flexível! Você pode seguir os cenários propostos (FTP, DVWA, SMB) ou adaptar à sua realidade: experimentar outras ferramentas, criar novas wordlists, explorar módulos/serviços diferentes, ou apenas documentar em detalhes o que aprendeu, com estudos, reflexões e exemplos de código. O mais importante é demonstrar seu entendimento e compartilhar sua jornada de aprendizado!

Softwares e sistemas usados:
  Kali Linux, Distro Ethical Hacking da Cisco Network Academy,
  (DVWA), Damn Vulnerable Web Application,
  Burp Suite Community Edition

Todo o processo foi documentado e explicado, bem como fotografado para melhor entendimento.

Início:

1# Configuração do Kali Linux com BurpSuite já instalado. 
  Para isso o usuário poderá baixar a versão disponibilizada pelo curso Santander Cybersegurança ou outras versões. Eu particularmente uso a versão criada pela Cisco Networking Academy, Ethical Hacking, que já contempla todos ambientes de testes e ferramentas para estudo.
  A versão para download encontra-se na seguinte página: 
  https://www.netacad.com/resources/lab-downloads

  Para criar o ambiente de testes usando a imagem do sistema Kali Linux usaremos o Oracle Virtual Box:
  https://www.oracle.com/br/virtualization/technologies/vm/downloads/virtualbox-downloads.html

2# Configurando o Bursuit para ataque Brute Force
  Primeiramente iniciaremos o Burpsuit Community Edition.
  Após sua inicialização o usuário deverá deixar em "Temporary Project" clickar em Next. (Imagem 1)
  Clickar em Start Burp. (Imagem 2)
  Após isso a tela inicial do Burp Suite aparecerá (imagem 3)

3# Configurações iniciais
  Após isso a tela inicial do Burp Suite aparecerá.
  Dentro da interface vá até a aba Proxy  (Imagem 4)
  Clique em Open Browser
  

4# Configurando os campos de entrada do brute force 1
  Dentro do navegador do Burp Suite vá para a página do DVWA
  No meu sistema o Ip do servidor local é http://10.6.6.13/security.php (Imagem 5)
  Vá até a aba "Brute Force" do site (Imagem 6)
  Dentro do Burp Suite clique no botão "intercept is off"
  Vá até o site do DVWA novamente e entre qualquer valor dentro dos campos "Username" e "Password"
  Após isso o Bursuit capturará as entradas do site com os campos necessários para o ataque de Brute Force

5# Configurando os campos de entrada do brute force 2
  clique com o mouse direito na tela e escolha a opção "Send to Intruder"(imagem 7)
  Dentro da aba do Intruder clique no botão "Clear §"
  Clique no botão " Add §" e adicione os dois campos de entrada com os valores que você entrou (Imagem 8)
  Altere o "Attacktype" para "Cluster Bomb"

6# Configurando os campos de entrada do brute force 3
  Altere o "Payload Type" para "Runtime file"
  Insira a Worlist em "Payload Settings [Runtime file]" (Imagem 9)
  Eu usei uma wordlist própria adaptada da fasttrack2, você pode usar qualquer wordlist que achar apropriada como a rockyou ou outras.
  O "Payload set" trata-se dos campos de entrada, como temos dois campos o número um será o username e o número dois o password.
  Altere o "payload set" para 2 deixe o "Payload type" em Runtime file também.
  Escolha a wordlist em "Payload Settings [Runtime file]"

7# Rodando o ataque de força bruta
  Clique em Start attack
  Após isso o programa iniciará uma lista de entradas nos campos
  A senha e usuário serão encontrados pela diferença do tamanho da saída do html
    Explicação: Entradas erradas resultarão no mesmo resultado "Lenght" enquanto um possível resultado positivo terá um valor diferenciado.
    No meu sistema após 226 entradas o resultado do "Lenght" apresentou-se alterado, resultado exatamente no ID e Senha que estava procurando. (Imagem 10)

Existem diversas outras configurações, sendo possível burlar sistemas de IDS e IPS, sendo necessário o estudo do sistema a ser atacado para a melhor configuração.
A plataforma do DVWA apresenta diversos níveis diferentes de dificuldade de brute force, para praticar o usuário poderá tentar quebrar a segurança dos outros níveis, através de configurações adicionais.

Obrigado.
    
    
  
  
  



  
