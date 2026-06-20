# Primera etapa: Construccion del build
# Se escoge la imagen ligera para node

FROM node:20-alpine AS builder

# Carpeta de trabajo

WORKDIR /app

# Se copia primero los archivos de las dependencias

COPY package*.json ./

# Instalacion de las dependencias

RUN npm install

# Copiamos el resto de archivos de la app

COPY . .

# Genera los archivos estaticos de la app

RUN npm run build

# Segunda etapa: Servidor de produccion con nginx

FROM nginx:alpine

# Copiamos el artefacto de la etapa anterior a la carpeta publica de nginx

COPY --from=builder /app/build /usr/share/nginx/html

# Exponemos el puerto 80 la app del frontend

EXPOSE 80

# Se arranca el servicio de nginx

CMD ["nginx", "-g", "daemon off;"]