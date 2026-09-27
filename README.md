# DriverPro SaaS — GitHub + Vercel + Supabase

MVP de controle financeiro e rastreamento GPS para motorista de aplicativo.

## 1. Supabase
1. Crie um projeto em https://supabase.com/.
2. Abra SQL Editor.
3. Cole e execute `supabase/schema.sql`.
4. Em Project Settings > API copie Project URL e anon public key.

## 2. Teste local
Instale Node.js 20+.

```bash
npm install
cp .env.example .env.local
npm run dev
```

Preencha `.env.local`:

```env
VITE_SUPABASE_URL=https://SEU-PROJETO.supabase.co
VITE_SUPABASE_ANON_KEY=SUA-ANON-KEY
```

Abra a URL mostrada pelo Vite, normalmente `http://localhost:5173`.

## 3. GitHub
Crie um repositório e envie todos os arquivos deste projeto. Não envie `.env.local`.

## 4. Vercel
Importe o repositório na Vercel. Em Settings > Environment Variables adicione:

- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_ANON_KEY`

Depois faça Deploy.

## 5. GPS
O navegador exige HTTPS (ou localhost) e permissão de localização. O MVP registra pontos durante o turno e grava-os no Supabase quando o usuário estiver autenticado.

### Limitação importante
Um navegador/PWA não é a solução mais confiável para rastreamento contínuo com tela bloqueada. Para uso profissional, a próxima etapa é um app Android/iOS com localização em segundo plano.

## Estrutura
- `src/main.js`: aplicação, autenticação, GPS e financeiro.
- `src/style.css`: interface responsiva.
- `supabase/schema.sql`: tabelas e RLS.
- `vercel.json`: configuração de SPA.
