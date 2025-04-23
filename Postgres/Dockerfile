# Utiliza a imagem oficial mais recente do PostgreSQL como base.
FROM postgres:13

# Defina variáveis de ambiente para configurar o PostgreSQL
ENV POSTGRES_DB=myDB
ENV POSTGRES_USER=user
ENV POSTGRES_PASSWORD=admin

# Copie o script de inicialização para o diretório de inicialização do PostgreSQL
COPY init.sql /docker-entrypoint-initdb.d/

# Exponha a porta padrão do PostgreSQL
EXPOSE 5432