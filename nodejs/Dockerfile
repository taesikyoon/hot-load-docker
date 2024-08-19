# NestJS Dockerfile
FROM node:20-alpine

# ffmpeg 6.1.1 이상 버전을 위한 프리빌트 바이너리 다운로드 및 설치
RUN apk add --no-cache curl xz && \
    curl -L https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-amd64-static.tar.xz | tar xJ && \
    cp ./ffmpeg*/ffmpeg /usr/local/bin/ffmpeg && \
    cp ./ffmpeg*/ffprobe /usr/local/bin/ffprobe && \
    rm -rf ./ffmpeg*

# Node.js 애플리케이션 파일 복사 및 설치
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .

# 앱 실행
CMD ["npm", "start:dev"]
