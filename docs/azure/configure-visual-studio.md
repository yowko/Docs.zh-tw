---
title: 使用 .NET 設定適用于 Azure 開發的 Visual Studio
description: 本文可協助您設定適用于 Azure 開發的 Visual Studio，包括將正確的工作負載安裝並連接 Visual Studio 至您的 Azure 帳戶
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 986469bd07657d968045465803047dc21d76dd62
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701108"
---
# <a name="configure-visual-studio-for-azure-development-with-net"></a><span data-ttu-id="4fe70-103">使用 .NET 設定適用于 Azure 開發的 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4fe70-103">Configure Visual Studio for Azure development with .NET</span></span>

<span data-ttu-id="4fe70-104">Visual Studio 包含可協助您在 Azure 上開發和部署應用程式的工具。</span><span class="sxs-lookup"><span data-stu-id="4fe70-104">Visual Studio includes tooling to help with the development and deployment of applications on Azure.</span></span>  <span data-ttu-id="4fe70-105">本指南將協助您確定已針對 Azure 開發正確設定 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4fe70-105">This guide will help you make sure that you have Visual Studio properly configured for Azure development.</span></span>

### <a name="download-visual-studio-2019"></a><span data-ttu-id="4fe70-106">下載 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="4fe70-106">Download Visual Studio 2019</span></span>

<span data-ttu-id="4fe70-107">如果您已經安裝 Visual Studio 2019，可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="4fe70-107">If you already have Visual Studio 2019 installed, you can skip this step.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4fe70-108">下載 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="4fe70-108">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="install-azure-workloads"></a><span data-ttu-id="4fe70-109">安裝 Azure 工作負載</span><span class="sxs-lookup"><span data-stu-id="4fe70-109">Install Azure workloads</span></span>

<span data-ttu-id="4fe70-110">啟動 **Visual Studio 安裝程式** ，並驗證您已安裝 **Azure 開發** 和 **ASP.NET 和 網頁程式開發** 的工作負載。</span><span class="sxs-lookup"><span data-stu-id="4fe70-110">Launch the **Visual Studio Installer** and validate that you have the workloads **Azure development** and **ASP.NET and web development** are installed.</span></span>  <span data-ttu-id="4fe70-111">如果未安裝這些工作負載的其中一個，請選取這些工作負載來進行安裝。</span><span class="sxs-lookup"><span data-stu-id="4fe70-111">If either of these workloads is not installed, select these workloads to install them.</span></span>

![Visual Studio 安裝程式的螢幕擷取畫面，其中顯示已選取的 Azure 開發和 ASP.NET 和 Web 開發工作負載](./media/visual-studio-installer-azure-development.png)

### <a name="authenticate-visual-studio-with-azure"></a><span data-ttu-id="4fe70-113">使用 Azure 驗證 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4fe70-113">Authenticate Visual Studio with Azure</span></span>

<span data-ttu-id="4fe70-114">透過 Visual Studio 來對應用程式進行偵錯工具時，Visual Studio 可以使用您的 Azure 帳戶來驗證和存取 Azure 資源。</span><span class="sxs-lookup"><span data-stu-id="4fe70-114">When debugging apps through Visual Studio, Visual Studio can use your Azure account to authenticate and access Azure Resources with.</span></span>  <span data-ttu-id="4fe70-115">當您直接從 Visual Studio 將應用程式發佈至 Azure 時，也會使用此帳戶。</span><span class="sxs-lookup"><span data-stu-id="4fe70-115">This account is also used when you publish apps directly from Visual Studio to Azure.</span></span>

<span data-ttu-id="4fe70-116">若要從 Visual Studio 驗證您的 Azure 帳戶，請選取 [**工具**  >  **選項**] 功能表來啟動 [**選項**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4fe70-116">To authenticate your Azure account from Visual Studio, select the **Tools** > **Options** menu to launch the **Options** dialog.</span></span> <span data-ttu-id="4fe70-117">流覽至 `Azure Service Authentication` 選項，然後使用您的 Azure 帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="4fe70-117">Navigate to the `Azure Service Authentication` options and sign in using your Azure account.</span></span>

![顯示 Azure 登入之 [Visual Studio 選項] 對話方塊的螢幕擷取畫面](./media/visual-studio-azure-login-dialog.png)

### <a name="next-steps"></a><span data-ttu-id="4fe70-119">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4fe70-119">Next steps</span></span>

<span data-ttu-id="4fe70-120">如果您也使用 [Visual Studio Code](https://code.visualstudio.com/) 在 .net 或任何其他語言中進行開發，您也應該 [設定適用于 Azure 開發的 Visual Studio Code](./configure-vs-code.md)。</span><span class="sxs-lookup"><span data-stu-id="4fe70-120">If you also use [Visual Studio Code](https://code.visualstudio.com/) for development in .NET or any other language, you should also [configure Visual Studio Code for Azure development](./configure-vs-code.md).</span></span> <span data-ttu-id="4fe70-121">否則，請繼續 [安裝 Azure CLI](./install-azure-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="4fe70-121">Otherwise, proceed to [Installing the Azure CLI](./install-azure-cli.md).</span></span>
