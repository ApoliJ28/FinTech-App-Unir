# Imagen base ligera para node
FROM node:20-alpine

# carpeta de trabajo
WORKDIR /app

# Copiamos solo primero los archivos de dependencias
COPY package*.json ./

# Intalacion limpia sin las dependencias de desarrollo
RUN npm install --omit=dev

# Copiamos el resto del codigo
COPY . .

# Se expone el puerto 3001 de la app
EXPOSE 3001

# Comando de ejecucion del backend
CMD ["npm", "start"]