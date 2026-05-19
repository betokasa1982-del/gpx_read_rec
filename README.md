# GPX Navigator Pro 📍

App de navegação por rota GPX com detecção automática de paradas e cronômetro.
Funciona **offline** no Android como app instalado (PWA).

---

## 📲 Como instalar no Android (2 opções)

### Opção A — GitHub Pages (recomendado, gratuito)

> Requer conta no GitHub (gratuita).

1. Acesse https://github.com e crie uma conta (se não tiver)
2. Clique em **"New repository"**
   - Nome: `gpx-nav` (ou qualquer nome)
   - Marque **"Public"**
   - Clique **"Create repository"**
3. Clique em **"uploading an existing file"**
4. Arraste **todos os arquivos desta pasta** para a área de upload:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icon-192.png`
   - `icon-512.png`
5. Clique em **"Commit changes"**
6. Vá em **Settings → Pages → Source → "Deploy from branch"**
   - Branch: `main`, pasta: `/ (root)`
   - Clique **Save**
7. Aguarde ~1 minuto. O endereço do app será:
   ```
   https://SEU-USUARIO.github.io/gpx-nav/
   ```
8. **No tablet/celular Android**, abra esse endereço no **Chrome**
9. Chrome mostrará um banner **"Adicionar à tela inicial"** → toque nele
10. ✅ App instalado! Aparece como ícone na tela inicial

---

### Opção B — Servidor local (sem internet, PC + Android na mesma rede Wi-Fi)

> Requer Python instalado no PC.

1. Abra o terminal na pasta dos arquivos do app
2. Execute:
   ```bash
   python -m http.server 8080
   ```
3. Descubra o IP do seu PC:
   - Windows: `ipconfig` → procure "Endereço IPv4" (ex: `192.168.1.10`)
   - Linux/Mac: `hostname -I`
4. No Android, abra o Chrome e acesse:
   ```
   http://192.168.1.10:8080
   ```

> ⚠️ **Nota**: em servidor local (http://) o GPS pode não funcionar no Android.
> Use a Opção A para GPS completo. Para uso em Wi-Fi interno corporativo, consulte
> como configurar HTTPS com certificado autoassinado.

---

## 🗺️ Como usar

### 1. Converter rodagem → GPX (no PC)
```bash
python conversor_mat_gpx.py rodagem01.mat
# Gera: rodagem01.gpx
```

### 2. Transferir o .gpx para o Android
- E-mail, WhatsApp, Google Drive, cabo USB — qualquer método

### 3. No app
1. Toque em **📂** e selecione o arquivo `.gpx`
2. A rota aparece no mapa com marcadores numerados nas paradas
3. Toque em **▶ GPS** para iniciar a navegação em tempo real
4. O app detecta automaticamente quando você chega em cada parada
5. O cronômetro inicia sozinho (configurável)
6. Arraste o **painel inferior** para cima para ver as paradas e timers
7. Toque **↓ CSV** para exportar tempos cronometrados

---

## ⚙️ Configurações de navegação (aba GPS)

| Configuração | Descrição | Padrão |
|---|---|---|
| Raio de chegada | Distância (m) para detectar chegada | 80 m |
| Auto-iniciar timer | Inicia cronômetro ao chegar | Sim |
| Seguir posição | Mapa segue sua posição | Sim |
| Zoom | Nível de zoom na navegação | 17 |

---

## 📁 Arquivos

| Arquivo | Descrição |
|---|---|
| `index.html` | App principal |
| `manifest.json` | Configuração PWA (ícone, nome, cor) |
| `sw.js` | Service worker (cache offline) |
| `icon-192.png` | Ícone do app (tela inicial) |
| `icon-512.png` | Ícone do app (splash screen) |
| `conversor_mat_gpx.py` | Conversor de rodagem .mat → .gpx |
