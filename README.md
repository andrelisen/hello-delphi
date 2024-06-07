//Para instalar o AWS CLI no Windows Server Delphi
Invoke-WebRequest "https://awscli.amazonaws.com/AWSCLIV2.msi" -OutFile "C:\AWSCLIV2.msi"
Start-Process "msiexec.exe" -ArgumentList "/i C:\AWSCLIV2.msi /quiet" -NoNewWindow -Wait
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine")


//É preciso criar um VPC Endpoint 
Service: com.amazonaws.us-east-1.s3
e colocar ele na tabela de rotas da subnet privada
E também um Service: ssm.us-east-1.amazonaws.com

//É preciso criar uma role com: (SSMRoleInstance)
- Acesso ao SSM - Com isso consigo me conectar na instância EC2 sem precisar de bastion e/ou está em suma subnet publica.
- Acesso full ao S3 - Com isso eu consigo copiar os arquivos para dentro da minha EC2

////////////////////////////////////////////////////////////////////////////////////////////////////////////////
- Agora preciso ter um jeito de deixar as app baterem na porta 9000 e conseguir fazer isso de uma outra instancia ec2: Criar um SG e colocar ALL Traffic e especificar o endereço IP da outra instância que deseja acessar a instância com a aplicação em Delphi

* Notei que toda vez que encerro a sessão de conexão ssm eu preciso instalar o aws cli de novo *

//Copiar o arquivo .exe do S3 para o servidor
aws s3 cp s3://hello-delphi/hello_delphi.exe .

//Endereços IPs & Security Groups
windows-server-delphi: 10.0.143.160
windows-server-curl: 10.0.139.34

//Dar permissão no SG do windows-server-delphi ao IP 
//Dar permissão no SG do windows-server-curl ao IP 

//No windows-server-curl quero pingar o windows-server-delphi
ping 
Invoke-WebRequest -Uri "endereço-ip:9000/ping"

//No windows-server-delphi quero pingar o windows-server-curl
ping 