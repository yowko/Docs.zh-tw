---
title: 使用 .NET 設定適用于 Azure 開發的 Visual Studio Code
description: 本文可協助您設定 Azure 開發的 Visual Studio Code，包括在 VS Code 中安裝及設定正確的外掛程式。
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 65ced99befe12d137062b4ea6a59a1ccd3099e0b
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701105"
---
# <a name="configure-visual-studio-code-for-azure-development"></a><span data-ttu-id="f69ee-103">設定適用于 Azure 開發的 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f69ee-103">Configure Visual Studio Code for Azure development</span></span>

<span data-ttu-id="f69ee-104">如果您要使用 Visual Studio Code （不論是針對 .NET 開發）使用像是角度、回應或 Vue 等架構來建立單一頁面應用程式，或是以 Python 等其他語言撰寫應用程式，則您會想要設定 Azure 開發的 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="f69ee-104">If you are using Visual Studio Code, whether for .NET development, for building single page applications using frameworks like Angular, React or Vue, or for writing applications in another language like Python, you will want to configure Visual Studio Code for Azure development.</span></span>

### <a name="download-visual-studio-code"></a><span data-ttu-id="f69ee-105">下載 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f69ee-105">Download Visual Studio Code</span></span>

<span data-ttu-id="f69ee-106">如果您已經安裝 Visual Studio Code，可以略過此步驟</span><span class="sxs-lookup"><span data-stu-id="f69ee-106">If you already have Visual Studio Code installed, you can skip this step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f69ee-107">下載 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f69ee-107">Download Visual Studio Code</span></span>](https://code.visualstudio.com/download)

### <a name="install-the-azure-tools-extension-pack"></a><span data-ttu-id="f69ee-108">安裝 Azure Tools 擴充功能套件</span><span class="sxs-lookup"><span data-stu-id="f69ee-108">Install the Azure Tools Extension Pack</span></span>

<span data-ttu-id="f69ee-109">[Azure Tools 擴充套件](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)包含的延伸模組可搭配使用 Azure App Service、Azure Functions、Azure 儲存體、Cosmos DB 和 Azure 虛擬機器，全都放在一個方便的套件中。</span><span class="sxs-lookup"><span data-stu-id="f69ee-109">The [Azure Tools Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) contains extensions for working with Azure App Service, Azure Functions, Azure Storage, Cosmos DB, and Azure Virtual Machines all in one convenient package.</span></span>

<span data-ttu-id="f69ee-110">若要從 Visual Studio Code 安裝延伸模組：</span><span class="sxs-lookup"><span data-stu-id="f69ee-110">To install the extension from Visual Studio Code:</span></span>

1. <span data-ttu-id="f69ee-111">按 <kbd>Ctrl + Shift + X</kbd> 以開啟 [ **擴充** 功能] 視窗。</span><span class="sxs-lookup"><span data-stu-id="f69ee-111">Press <kbd>Ctrl+Shift+X</kbd> to open the **Extensions** window.</span></span>
1. <span data-ttu-id="f69ee-112">搜尋 *Azure Tools* 擴充功能。</span><span class="sxs-lookup"><span data-stu-id="f69ee-112">Search for the *Azure Tools* extension.</span></span>
1. <span data-ttu-id="f69ee-113">選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f69ee-113">Select the **Install** button.</span></span>

![Visual Studio Code 的螢幕擷取畫面，其中顯示搜尋 Azure Tools 擴充功能套件的延伸模組面板](./media/visual-studio-code-azure-tools.png)

<span data-ttu-id="f69ee-115">若要深入瞭解如何在 Visual Studio Code 中安裝擴充功能，請參閱 Visual Studio Code 網站上的 [延伸模組 Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery) 檔。</span><span class="sxs-lookup"><span data-stu-id="f69ee-115">To learn more about installing extensions in Visual Studio Code, refer to the [Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery) document on the Visual Studio Code website.</span></span>

### <a name="sign-in-to-your-azure-account-with-azure-tools"></a><span data-ttu-id="f69ee-116">使用 Azure Tools 登入您的 Azure 帳戶</span><span class="sxs-lookup"><span data-stu-id="f69ee-116">Sign in to your Azure account with Azure Tools</span></span>

<span data-ttu-id="f69ee-117">在左側面板上，您會看到 Azure 圖示。</span><span class="sxs-lookup"><span data-stu-id="f69ee-117">On the left hand panel, you'll see an Azure icon.</span></span> <span data-ttu-id="f69ee-118">選取此圖示，將會顯示 Azure 服務的控制台。</span><span class="sxs-lookup"><span data-stu-id="f69ee-118">Select this icon, and a control panel for Azure services will appear.</span></span> <span data-ttu-id="f69ee-119">選擇 [登 **入 Azure ...** ] 下的任何服務，在 Visual Studio Code 中完成 azure 工具的驗證程式。</span><span class="sxs-lookup"><span data-stu-id="f69ee-119">Choose **Sign in to Azure...** under any service to complete the authentication process for the Azure tools in Visual Studio Code.</span></span>

![顯示如何將 Azure tools 登入 Azure 的 Visual Studio Code 螢幕擷取畫面](./media/visual-studio-code-azure-login.png)

### <a name="next-steps"></a><span data-ttu-id="f69ee-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f69ee-121">Next steps</span></span>

<span data-ttu-id="f69ee-122">接下來，您會想要在您的工作站上安裝 Azure CLI。</span><span class="sxs-lookup"><span data-stu-id="f69ee-122">Next, you will want to install the Azure CLI on your workstation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f69ee-123">安裝 Azure CLI</span><span class="sxs-lookup"><span data-stu-id="f69ee-123">Install the Azure CLI</span></span>](./install-azure-cli.md)
