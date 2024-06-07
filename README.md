//Para instalar o AWS CLI no Windows Server
Invoke-WebRequest "https://awscli.amazonaws.com/AWSCLIV2.msi" -OutFile "C:\AWSCLIV2.msi"
Start-Process "msiexec.exe" -ArgumentList "/i C:\AWSCLIV2.msi /quiet" -NoNewWindow -Wait
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine")


//É preciso criar um VPC Endpoint 
Service: com.amazonaws.us-east-1.s3
e colocar ele na tabela de rotas da subnet privada

//É preciso criar uma role com:
- Acesso ao SSM
- Acesso full ao S3
- Com isso eu consigo copiar os arquivos para dentro da minha EC2

-Agora preciso ter um jeito de deixar as app baterem na porta 9000 e conseguir fazer isso de uma outra instancia ec2

Criar um SG e colocar ALL Traffic e especificar o endereço IP da outra instância que deseja acessar a instância com a aplicação em Delphi
