# Portfólio Pessoal - danciguer.com.br

Site de portfólio pessoal desenvolvido com Next.js, React e Material UI.

## 🚀 Tecnologias

- [Next.js](https://nextjs.org/) - Framework React com SSR/SSG
- [React](https://reactjs.org/) - Biblioteca JavaScript para interfaces
- [Material UI](https://mui.com/) - Biblioteca de componentes React
- [Emotion](https://emotion.sh/) - Biblioteca CSS-in-JS
- [Framer Motion](https://www.framer.com/motion/) - Biblioteca de animações
- [Formspree](https://formspree.io/) - Serviço para formulários de contato

## 📋 Requisitos

- Node.js 16.x ou superior
- npm ou yarn

## 🔧 Instalação

1. Clone o repositório:
```bash
git clone https://github.com/seu-usuario/danciguer-site.git
cd danciguer-site
```

2. Instale as dependências:
```bash
npm install
# ou
yarn install
```

3. Crie um arquivo `.env.local` baseado no `.env.example`:
```bash
cp .env.example .env.local
```

4. Execute o servidor de desenvolvimento:
```bash
npm run dev
# ou
yarn dev
```

5. Acesse [http://localhost:3000](http://localhost:3000) no navegador.

## 🏗️ Estrutura do Projeto

```
portfolio/
├─ public/            # Arquivos estáticos
├─ src/
│   ├─ components/    # Componentes React reutilizáveis
│   ├─ pages/         # Páginas e rotas Next.js
│   ├─ theme.js       # Configuração do tema MUI
│   └─ styles/        # Estilos globais
├─ .env.local         # Variáveis de ambiente (não versionado)
├─ .env.example       # Exemplo de variáveis de ambiente
└─ next.config.js     # Configuração do Next.js
```

## 🚢 Deploy

### Build para produção

```bash
npm run build
# ou
yarn build
```

### Deploy na VPS Ubuntu com Nginx

1. Faça o build do projeto:
```bash
npm run build
```

2. Transfira os arquivos para o servidor:
```bash
scp -r .next package.json package-lock.json next.config.js public usuario@seu-servidor:/caminho/para/app
```

3. No servidor, instale as dependências:
```bash
cd /caminho/para/app
npm install --production
```

4. Configure o Nginx:
```nginx
server {
    listen 80;
    server_name danciguer.com.br www.danciguer.com.br;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

5. Salve a configuração em `/etc/nginx/sites-available/danciguer` e crie um link simbólico:
```bash
sudo ln -s /etc/nginx/sites-available/danciguer /etc/nginx/sites-enabled/
```

6. Teste e reinicie o Nginx:
```bash
sudo nginx -t
sudo systemctl restart nginx
```

7. Configure o PM2 para manter o aplicativo em execução:
```bash
npm install -g pm2
pm2 start npm --name "danciguer-site" -- start
pm2 save
pm2 startup
```

## 📝 Recursos e Funcionalidades

- Landing page com seção hero
- Seção "Sobre Mim" com skills e download de currículo
- Portfólio de projetos com filtro por tecnologia
- Formulário de contato funcional
- Tema claro/escuro com persistência
- Design responsivo para todos dispositivos
- Animações suaves com Framer Motion
- SEO otimizado

## 🔒 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes. 