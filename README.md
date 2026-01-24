# AIDraft - AI-Powered Architectural Design Platform

AIDraft is a cutting-edge architectural design platform that integrates artificial intelligence to streamline and enhance the creative process for architects and designers. Our platform empowers you to effortlessly generate, optimize, and collaborate on sophisticated architectural designs with intuitive, AI-driven tools.

---

## ⚠️ IMPORTANT NOTICE - Azure API Keys Required

**This application requires Azure API keys to function. The deployed/live version will NOT work without your own API keys due to cost considerations.**

### To Use This Application:

1. **Clone this repository** to your local machine
2. **Set up your own Azure services** (Azure OpenAI & Azure Computer Vision)
3. **Add your API keys** to a `.env.local` file
4. **Run locally** using `npm run dev`

📋 **[Step-by-step setup guide available in SETUP.md](./SETUP.md)**

Azure AI services have associated costs. Please be aware of Azure pricing before setting up:
- [Azure OpenAI Pricing](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/openai-service/)
- [Azure Computer Vision Pricing](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/computer-vision/)

For demonstration purposes without Azure costs, the app includes fallback mock data when API calls fail.

---

## Application Architecture

![AIDraft Architecture](/app_architecture.png)

## Platform Features

![AIDraft Features](/cad_generator.png)

---

## 🚀 Features

-   **AI-Assisted Design:** Seamlessly generate and optimize floor plans, layouts, and interactive 3D models.
-   **Real-Time Collaboration:** Work collaboratively with team members simultaneously.
-   **Efficient Project Management:** Easily track project progress, manage tasks, and keep deadlines organized.
-   **Sustainability Insights:** Evaluate designs for energy efficiency and sustainable material usage.
-   **Automated Code Compliance:** Instantly verify designs against the latest building codes.
-   **Visualization & Rendering:** Create stunning, interactive 3D models with realistic rendering.

## 🛠 Tech Stack

-   **Frontend:** Next.js, React, TypeScript, Tailwind CSS
-   **UI Components:** Shadcn UI
-   **Visualization:** Three.js
-   **AI Integration:** Azure OpenAI, Azure Computer Vision

## 🚦 Getting Started

### Prerequisites

-   Node.js (v18+) and npm
-   Git
-   **Azure Account** with active subscription
-   **Azure OpenAI** resource with GPT-4 deployment
-   **Azure Computer Vision** resource

### Installation

1. Clone the repository:

```bash
git clone https://github.com/your-username/aidraft.git
cd aidraft
```

2. Install dependencies:

```bash
npm install
```

3. **Set up Azure Services** (Required):
   - Create an [Azure OpenAI resource](https://portal.azure.com/#create/Microsoft.CognitiveServicesOpenAI)
   - Deploy a GPT-4 model in your Azure OpenAI resource
   - Create an [Azure Computer Vision resource](https://portal.azure.com/#create/Microsoft.CognitiveServicesComputerVision)
   - Note down your API keys and endpoints

4. Create a `.env.local` file in the root directory:

```env
# App Settings
NEXT_PUBLIC_APP_URL=http://localhost:3000

# Azure OpenAI Configuration
AZURE_OPENAI_KEY=your_azure_openai_key
AZURE_OPENAI_ENDPOINT=https://your-resource-name.openai.azure.com
AZURE_OPENAI_DEPLOYMENT=your_deployment_name
AZURE_OPENAI_API_VERSION=2023-12-01-preview

# Azure Computer Vision
AZURE_VISION_KEY=your_azure_vision_key
AZURE_VISION_ENDPOINT=https://your-vision-resource.cognitiveservices.azure.com

# Authentication (Optional)
AUTH_SECRET=your_auth_secret_key
NEXTAUTH_URL=http://localhost:3000
```

5. Run the development server:

```bash
npm run dev
```

6. Visit [http://localhost:3000](http://localhost:3000) to access the app.

### ⚠️ Cost Management Tips

- Azure OpenAI charges per token used. Monitor your usage in the Azure portal.
- Set up spending limits and alerts in your Azure account.
- Use the mock data fallback for testing UI without incurring costs.
- Consider using Azure's free tier for initial testing (limited usage).

## ⚙️ Configuration Guide

### Agent Configuration

Customize the multi-agent system in `agent-config.ts`:

```ts
export const AZURE_SERVICES_CONFIG = {
    openai: {
        key: process.env.AZURE_OPENAI_KEY || "",
        endpoint: process.env.AZURE_OPENAI_ENDPOINT || "",
        deployment: process.env.AZURE_OPENAI_DEPLOYMENT || "gpt-4",
        apiVersion:
            process.env.AZURE_OPENAI_API_VERSION || "2023-12-01-preview",
    },
    vision: {
        key: process.env.AZURE_VISION_KEY || "",
        endpoint: process.env.AZURE_VISION_ENDPOINT || "",
    },
};

export const AGENT_CONFIG = {
    maxRetries: 2,
    defaultTemperature: 0.2,
    interpreterSystemPrompt: `You are an Architectural Interpreter Agent...`,
    designerSystemPrompt: `You are an Architectural Designer Agent...`,
    rendererSystemPrompt: `You are a 3D Rendering Agent...`,
};
```

### Setting Up Azure Services

📋 **For detailed step-by-step instructions, see [SETUP.md](./SETUP.md)**

**Quick Overview:**

**Azure OpenAI:**
-   Create an Azure OpenAI resource and deploy a GPT-4 model
-   Add your key and endpoint details to `.env.local`

**Azure Computer Vision:**
-   Set up an Azure Computer Vision resource
-   Update your key and endpoint in `.env.local`

## 📂 Project Structure

```
├── app/             # Next.js pages and app router
├── components/      # React UI components
├── lib/             # Utilities and helper functions
├── public/          # Static assets
├── styles/          # Global CSS and Tailwind styles
└── types/           # TypeScript types and interfaces
```

## 📃 Key Pages

-   `/` – Home Page
-   `/dashboard` – User Dashboard
-   `/projects` – Projects List
-   `/project/[id]` – Detailed Project View
-   `/cad-generator` – AI CAD Generation
-   `/team` – Team Management
-   `/analytics` – Usage Analytics
-   `/settings` – User Settings

## 🌳 Development Workflow

Create a feature branch:

```bash
git checkout -b feature/your-feature-name
```

Commit your changes:

```bash
git commit -m "Add your feature"
```

Push changes:

```bash
git push origin feature/your-feature-name
```

Open a pull request targeting the `main` branch.

## 🌍 Deployment

### Production Build

```bash
npm run build
npm start
```

### Deploying to Vercel

Install the Vercel CLI:

```bash
npm install -g vercel
```

Deploy your app:

```bash
vercel
```

## 🤝 Contributing

We enthusiastically welcome contributions! Please review `CONTRIBUTING.md` for guidance.

## 📜 License

This project is open-sourced under the MIT License.

---

Happy Designing with AIDraft! 🚧🏙✨
