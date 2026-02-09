# Snake Game

A simple, classic Snake game built with HTML, CSS, and JavaScript.

## How to Play

- Use arrow keys to control the snake
- Eat the red food to grow and score points
- Avoid hitting the walls or yourself
- Try to beat your high score!

## Running Locally

Simply open `index.html` in your web browser.

## Deploying to Azure

### Option 1: Azure Static Web Apps (Recommended - Free Tier Available)

**With GitHub:**
1. Push this code to a GitHub repository
2. Go to [Azure Portal](https://portal.azure.com)
3. Create a new "Static Web App"
4. Connect your GitHub repository
5. Set build configuration:
   - App location: `/`
   - No build command needed
   - Output location: leave empty
6. Azure will automatically deploy on every push

**Without GitHub (Manual Deploy):**
1. Install Azure CLI: `winget install Microsoft.AzureCLI`
2. Login: `az login`
3. Install Static Web Apps CLI: `npm install -g @azure/static-web-apps-cli`
4. Deploy: `swa deploy --app-location . --deployment-token <your-token>`

### Option 2: Azure Blob Storage (Static Website Hosting)

1. Install Azure CLI if not already installed
2. Login: `az login`
3. Create a storage account:
   ```
   az storage account create --name snakegame<uniqueid> --resource-group <your-rg> --location eastus --sku Standard_LRS
   ```
4. Enable static website hosting:
   ```
   az storage blob service-properties update --account-name snakegame<uniqueid> --static-website --index-document index.html
   ```
5. Upload files:
   ```
   az storage blob upload-batch --account-name snakegame<uniqueid> --source . --destination $web
   ```
6. Get the website URL:
   ```
   az storage account show --name snakegame<uniqueid> --query "primaryEndpoints.web" --output tsv
   ```

### Option 3: Azure App Service

1. Create a zip file of your game files
2. In Azure Portal, create a new "Web App"
3. Choose "Code" deployment and select Node or Static HTML runtime
4. Deploy using Azure CLI:
   ```
   az webapp up --name snake-game-<uniqueid> --html
   ```

## Features

- Responsive design
- Score tracking
- High score saved in browser
- Smooth gameplay
- Clean, modern UI

## Technologies Used

- HTML5 Canvas
- CSS3
- Vanilla JavaScript
- LocalStorage for high score persistence
