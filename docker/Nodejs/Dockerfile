FROM node:22

# Define o diretório de trabalho
WORKDIR /usr/src/app

# Copia apenas os arquivos da pasta src (onde estão o package.json e o código)
COPY src/package*.json ./

# Instala as dependências
RUN npm install

# Copia o restante da aplicação
COPY src .

# Expõe a porta
EXPOSE 3000

# Comando para rodar a aplicação
CMD [ "npm", "start" ]