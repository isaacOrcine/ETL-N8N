# Guia de Instalação do n8n Localmente no Windows

Este guia tem como objetivo ensinar o passo a passo para instalar o n8n localmente em um ambiente Windows. Além disso, incluímos um exemplo prático de um fluxo de uso do n8n que integra Google Drive, processamento de PDF e Google Calendar.

## 1. Instalando o n8n no Windows

### Passos para instalação:

1. **Abra o PowerShell como Administrador (procure por "cmd" na barra de pesquisa do Windows)"**.
2. **Execute o comando de instalação do n8n**:
   ```bash
   npx n8n
   ```
   > **Nota**: Esse comando instala e inicia o n8n localmente.

### Links úteis:

- [Documentação Oficial do n8n](https://docs.n8n.io/)

## 2. Criando Credenciais Necessárias

Para que o fluxo funcione, será necessário criar credenciais para os serviços abaixo:

### 2.1. Credenciais do Google Drive e Google Calendar

1. \*\*Acesse o \*\***[Google Cloud Console](https://console.cloud.google.com/)** e crie um projeto.
2. **Ative as APIs do Google Drive e do Google Calendar**.
3. **Configure as credenciais de OAuth 2.0** e copie o Client ID e Client Secret.
4. No n8n, crie uma nova credencial de OAuth 2.0 para Google Drive e Google Calendar.

### Links de ajuda:

- [Documentação de Credenciais do Google no n8n](https://docs.n8n.io/integrations/builtin/credentials/google/)
- [Configuração de credenciais no Google Cloud](https://developers.google.com/identity/protocols/oauth2)

## 3. Exemplo de Uso: Fluxo de Extração e Agendamento

### Descrição do fluxo

Este exemplo de fluxo no n8n faz o seguinte:

- Faz download de arquivos PDF do Google Drive.
- Extrai dados específicos dos PDFs.
- Processa as informações extraídas e cria entradas no Google Calendar.

### Estrutura do fluxo:

```json
{
  "nodes": [
    { "name": "Google Drive Download", "type": "googleDrive", "...": "..." },
    { "name": "Extract from PDF", "type": "extractFromFile", "...": "..." },
    { "name": "Schedule Trigger", "type": "scheduleTrigger", "...": "..." },
    { "name": "Code (Extrair informações)", "type": "code", "...": "..." },
    { "name": "Google Calendar", "type": "googleCalendar", "...": "..." }
  ]
}
```

### Importante

- **Crie as credenciais no n8n conforme o passo 2.1** para que o fluxo funcione corretamente.
- **Verifique se os IDs de arquivos do Google Drive e os dados extraídos correspondem ao seu cenário.**



