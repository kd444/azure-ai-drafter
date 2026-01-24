# Azure Services Setup Guide

This guide will walk you through setting up the required Azure services to run this application.

## ⚠️ Important Notes

- **Azure services have associated costs.** Review the pricing links before proceeding.
- **Set up billing alerts** in Azure to monitor spending.
- **Consider starting with free tier** options when available.

---

## Prerequisites

1. An Azure account ([Sign up for free](https://azure.microsoft.com/free/))
2. Node.js 18+ installed
3. Git installed
4. This repository cloned locally

---

## Step 1: Create Azure OpenAI Resource

### 1.1 Navigate to Azure Portal
- Go to [Azure Portal](https://portal.azure.com)
- Sign in with your Microsoft account

### 1.2 Create Azure OpenAI Resource
1. Click **"Create a resource"**
2. Search for **"Azure OpenAI"**
3. Click **"Create"**
4. Fill in the required information:
   - **Subscription**: Select your subscription
   - **Resource Group**: Create new or select existing
   - **Region**: Choose a region (e.g., East US, West Europe)
   - **Name**: Enter a unique name (e.g., `myapp-openai`)
   - **Pricing Tier**: Select your tier (Standard S0)
5. Click **"Review + create"** then **"Create"**
6. Wait for deployment to complete

### 1.3 Deploy a Model
1. Go to your Azure OpenAI resource
2. Click on **"Go to Azure OpenAI Studio"**
3. Navigate to **"Deployments"** in the left menu
4. Click **"+ Create new deployment"**
5. Select model:
   - **Model**: Choose **GPT-4** (recommended) or GPT-3.5-Turbo
   - **Deployment name**: Enter a name (e.g., `gpt-4`)
   - **Model version**: Use default or latest
6. Click **"Create"**

### 1.4 Get API Keys
1. In Azure Portal, go to your OpenAI resource
2. Click on **"Keys and Endpoint"** in the left menu
3. Copy:
   - **KEY 1** (your API key)
   - **Endpoint** (your endpoint URL)
   - Note your **deployment name** from step 1.3

**Pricing**: [Azure OpenAI Pricing Details](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/openai-service/)

---

## Step 2: Create Azure Computer Vision Resource

### 2.1 Create Computer Vision Resource
1. In Azure Portal, click **"Create a resource"**
2. Search for **"Computer Vision"**
3. Click **"Create"**
4. Fill in the required information:
   - **Subscription**: Select your subscription
   - **Resource Group**: Use same as OpenAI or create new
   - **Region**: Choose same region as OpenAI (recommended)
   - **Name**: Enter a unique name (e.g., `myapp-vision`)
   - **Pricing Tier**: Select F0 (free) or S1 (standard)
5. Click **"Review + create"** then **"Create"**
6. Wait for deployment to complete

### 2.2 Get API Keys
1. Go to your Computer Vision resource
2. Click on **"Keys and Endpoint"** in the left menu
3. Copy:
   - **KEY 1** (your API key)
   - **Endpoint** (your endpoint URL)

**Pricing**: [Azure Computer Vision Pricing Details](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/computer-vision/)

---

## Step 3: Configure Application

### 3.1 Create Environment File
1. In your project root, copy the example file:
   ```bash
   cp .env.local.example .env.local
   ```

### 3.2 Update .env.local
Open `.env.local` and fill in your values:

```env
# Azure OpenAI Configuration
AZURE_OPENAI_KEY=<YOUR_OPENAI_KEY_FROM_STEP_1.4>
AZURE_OPENAI_ENDPOINT=<YOUR_OPENAI_ENDPOINT_FROM_STEP_1.4>
AZURE_OPENAI_DEPLOYMENT=<YOUR_DEPLOYMENT_NAME_FROM_STEP_1.3>
AZURE_OPENAI_API_VERSION=2023-12-01-preview

# Azure Computer Vision
AZURE_VISION_KEY=<YOUR_VISION_KEY_FROM_STEP_2.2>
AZURE_VISION_ENDPOINT=<YOUR_VISION_ENDPOINT_FROM_STEP_2.2>
```

### 3.3 Example Configuration
```env
# Example (replace with your actual values)
AZURE_OPENAI_KEY=a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6
AZURE_OPENAI_ENDPOINT=https://myapp-openai.openai.azure.com
AZURE_OPENAI_DEPLOYMENT=gpt-4
AZURE_OPENAI_API_VERSION=2023-12-01-preview

AZURE_VISION_KEY=z9y8x7w6v5u4t3s2r1q0p9o8n7m6l5k4
AZURE_VISION_ENDPOINT=https://myapp-vision.cognitiveservices.azure.com
```

---

## Step 4: Run the Application

### 4.1 Install Dependencies
```bash
npm install
```

### 4.2 Start Development Server
```bash
npm run dev
```

### 4.3 Access the Application
Open your browser and navigate to:
```
http://localhost:3000
```

---

## Cost Management Tips

### Monitor Your Spending
1. Set up billing alerts in Azure Portal
2. Check usage regularly in Azure OpenAI Studio
3. Review the [Azure Cost Management](https://portal.azure.com/#blade/Microsoft_Azure_CostManagement/Menu/overview) dashboard

### Optimize Costs
- **Use GPT-3.5-Turbo** instead of GPT-4 for lower costs
- **Enable caching** where possible
- **Set token limits** in your prompts
- **Use Computer Vision F0 tier** (free) for testing
- **Delete resources** when not in use

### Token Usage Estimates
- GPT-4: ~$0.03 per 1K tokens (input), ~$0.06 per 1K tokens (output)
- GPT-3.5-Turbo: ~$0.0015 per 1K tokens (input), ~$0.002 per 1K tokens (output)

---

## Troubleshooting

### "Unauthorized" or "401" errors
- Verify your API keys are correct
- Check that your Azure resources are deployed and active
- Ensure your subscription is active

### "Quota exceeded" errors
- Check your Azure OpenAI quota limits
- Request quota increase in Azure Portal if needed
- Wait for quota to reset (usually daily/monthly)

### "Model not found" errors
- Verify the deployment name matches exactly
- Ensure the model is fully deployed in Azure OpenAI Studio
- Check that the API version is correct

### Application shows mock data
- This is the fallback behavior when Azure API calls fail
- Check console logs for specific error messages
- Verify all environment variables are set correctly

---

## Additional Resources

- [Azure OpenAI Documentation](https://learn.microsoft.com/en-us/azure/cognitive-services/openai/)
- [Azure Computer Vision Documentation](https://learn.microsoft.com/en-us/azure/cognitive-services/computer-vision/)
- [Azure Pricing Calculator](https://azure.microsoft.com/en-us/pricing/calculator/)
- [Azure Free Account](https://azure.microsoft.com/free/)

---

## Support

If you encounter issues:
1. Check the troubleshooting section above
2. Review Azure service status: https://status.azure.com/
3. Check application logs in browser console
4. Review Azure resource logs in Azure Portal

---

**Remember**: Always monitor your Azure spending and set up alerts to avoid unexpected charges!
