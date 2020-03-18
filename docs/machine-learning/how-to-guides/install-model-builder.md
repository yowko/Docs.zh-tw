---
title: 如何安裝模型建立器
description: 了解如何安裝 ML.NET 模型建立器工具
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: b944d7f6044553251132824e7e4213119e34500e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848648"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="8b07d-103">了解如何安裝 ML.NET 模型建立器</span><span class="sxs-lookup"><span data-stu-id="8b07d-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="8b07d-104">了解如何安裝 ML.NET 模型建立器，將機器學習服務新增至您的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8b07d-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="8b07d-105">模型產生器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="8b07d-105">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8b07d-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="8b07d-106">Prerequisites</span></span>

- <span data-ttu-id="8b07d-107">視覺工作室 2017 版本 15.9.12 或更高版本 / 視覺工作室 2019</span><span class="sxs-lookup"><span data-stu-id="8b07d-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="8b07d-108">.NET 核心 2.1 SDK 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="8b07d-108">.NET Core 2.1 SDK or later.</span></span>

> [!NOTE]
> <span data-ttu-id="8b07d-109">.NET 核心 3.0 SDK 當前不受支援。</span><span class="sxs-lookup"><span data-stu-id="8b07d-109">.NET Core 3.0 SDK is not currently supported.</span></span>

## <a name="limitations"></a><span data-ttu-id="8b07d-110">限制</span><span class="sxs-lookup"><span data-stu-id="8b07d-110">Limitations</span></span>

- <span data-ttu-id="8b07d-111">ML.NET 模型建立器延伸模組目前僅適用於 Windows 的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8b07d-111">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="8b07d-112">1 GB 的定型資料集限制</span><span class="sxs-lookup"><span data-stu-id="8b07d-112">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="8b07d-113">SQL Server 的定型上限為 10 萬筆資料列</span><span class="sxs-lookup"><span data-stu-id="8b07d-113">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="8b07d-114">不支援 Microsoft SQL Server Data Tools for Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="8b07d-114">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="8b07d-115">安裝</span><span class="sxs-lookup"><span data-stu-id="8b07d-115">Install</span></span>

<span data-ttu-id="8b07d-116">您可透過 Visual Studio Marketplace，或從 Visual Studio 安裝 ML.NET 模型建立器。</span><span class="sxs-lookup"><span data-stu-id="8b07d-116">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="8b07d-117">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="8b07d-117">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="8b07d-118">從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07) 下載</span><span class="sxs-lookup"><span data-stu-id="8b07d-118">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="8b07d-119">遵循提示安裝到個別的 Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="8b07d-119">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="8b07d-120">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="8b07d-120">Visual Studio 2017</span></span>

1. <span data-ttu-id="8b07d-121">在功能表列中，選擇 **"工具** > **擴展"和"更新"**</span><span class="sxs-lookup"><span data-stu-id="8b07d-121">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 打開擴展管理器對話方塊](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="8b07d-123">在 [延伸模組和更新]\*\* 提示內部，選取「線上」\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="8b07d-123">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="8b07d-124">在搜尋列中，搜尋「ML.NET 模型建立器」\*\*，然後從結果中選取 ML.NET 模型建立器 (預覽)</span><span class="sxs-lookup"><span data-stu-id="8b07d-124">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![VS2017 在擴展管理器對話方塊中搜索並安裝模型產生器擴展](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="8b07d-126">遵循提示完成安裝</span><span class="sxs-lookup"><span data-stu-id="8b07d-126">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="8b07d-127">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="8b07d-127">Visual Studio 2019</span></span>

1. <span data-ttu-id="8b07d-128">在功能表列上，選擇 **"擴展** > **管理擴展"**</span><span class="sxs-lookup"><span data-stu-id="8b07d-128">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 打開擴展管理器對話方塊](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="8b07d-130">在 [延伸模組和更新]\*\* 提示內部，選取「線上」\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="8b07d-130">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="8b07d-131">在搜尋列中鍵入「ML.NET 模型建立器」\*\*，選取 ML.NET 模型建立器 (預覽)</span><span class="sxs-lookup"><span data-stu-id="8b07d-131">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 在擴展管理器對話方塊中搜索並安裝模型產生器擴展](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="8b07d-133">遵循提示完成安裝</span><span class="sxs-lookup"><span data-stu-id="8b07d-133">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="8b07d-134">解除安裝</span><span class="sxs-lookup"><span data-stu-id="8b07d-134">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="8b07d-135">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="8b07d-135">Visual Studio 2017</span></span>

1. <span data-ttu-id="8b07d-136">在功能表列上，選擇 **"工具** > **擴展"和"更新"**</span><span class="sxs-lookup"><span data-stu-id="8b07d-136">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 打開管理擴展對話方塊](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="8b07d-138">在 [延伸模組和更新]\*\* 提示內部，展開「已安裝的」\*\* 節點，然後選取 [工具]\*\*</span><span class="sxs-lookup"><span data-stu-id="8b07d-138">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="8b07d-139">從工具清單選取 ML.NET 模型建立器 (預覽)，然後選取 [解除安裝]\*\*</span><span class="sxs-lookup"><span data-stu-id="8b07d-139">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2017 在擴展管理器對話方塊中搜索和卸載模型產生器擴展](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="8b07d-141">遵循提示完成解除安裝。</span><span class="sxs-lookup"><span data-stu-id="8b07d-141">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="8b07d-142">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="8b07d-142">Visual Studio 2019</span></span>

1. <span data-ttu-id="8b07d-143">在功能表列上，選擇 **"擴展** > **管理擴展"**</span><span class="sxs-lookup"><span data-stu-id="8b07d-143">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 打開管理擴展對話方塊](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="8b07d-145">在 [延伸模組和更新]\*\* 提示內部，展開「已安裝的」\*\* 節點，然後選取 [工具]\*\*</span><span class="sxs-lookup"><span data-stu-id="8b07d-145">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="8b07d-146">從工具清單選取 ML.NET 模型建立器 (預覽)，然後選取 [解除安裝]\*\*</span><span class="sxs-lookup"><span data-stu-id="8b07d-146">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2019 在擴展管理器對話方塊中搜索和卸載模型產生器擴展](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="8b07d-148">遵循提示完成解除安裝。</span><span class="sxs-lookup"><span data-stu-id="8b07d-148">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="8b07d-149">升級</span><span class="sxs-lookup"><span data-stu-id="8b07d-149">Upgrade</span></span>

<span data-ttu-id="8b07d-150">升級程序類似安裝程序。</span><span class="sxs-lookup"><span data-stu-id="8b07d-150">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="8b07d-151">從 Visual Studio Marketplace 或使用 Visual Studio 的延伸模組管理員下載最新版本。</span><span class="sxs-lookup"><span data-stu-id="8b07d-151">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
