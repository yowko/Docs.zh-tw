---
title: 如何安裝模型建立器
description: 了解如何安裝 ML.NET 模型建立器工具
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: a1034d294012b8df5ec778fc40602fe52223961d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774573"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="c62b6-103">了解如何安裝 ML.NET 模型建立器</span><span class="sxs-lookup"><span data-stu-id="c62b6-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="c62b6-104">了解如何安裝 ML.NET 模型建立器，將機器學習服務新增至您的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c62b6-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="c62b6-105">模型產生器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="c62b6-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="c62b6-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="c62b6-106">Pre-requisites</span></span>

- <span data-ttu-id="c62b6-107">Visual Studio 2017 15.9.12 版或更新版本/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="c62b6-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="c62b6-108">.NET Core 2.1 或更新版本的 SDK</span><span class="sxs-lookup"><span data-stu-id="c62b6-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="c62b6-109">限制</span><span class="sxs-lookup"><span data-stu-id="c62b6-109">Limitations</span></span>

- <span data-ttu-id="c62b6-110">ML.NET 模型建立器延伸模組目前僅適用於 Windows 的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="c62b6-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="c62b6-111">1 GB 的定型資料集限制</span><span class="sxs-lookup"><span data-stu-id="c62b6-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="c62b6-112">SQL Server 的定型上限為 10 萬筆資料列</span><span class="sxs-lookup"><span data-stu-id="c62b6-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="c62b6-113">不支援 Microsoft SQL Server Data Tools for Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c62b6-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="c62b6-114">安裝</span><span class="sxs-lookup"><span data-stu-id="c62b6-114">Install</span></span>

<span data-ttu-id="c62b6-115">您可透過 Visual Studio Marketplace，或從 Visual Studio 安裝 ML.NET 模型建立器。</span><span class="sxs-lookup"><span data-stu-id="c62b6-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="c62b6-116">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="c62b6-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="c62b6-117">從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07) 下載</span><span class="sxs-lookup"><span data-stu-id="c62b6-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="c62b6-118">遵循提示安裝到個別的 Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="c62b6-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="c62b6-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c62b6-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="c62b6-120">在功能表列上，選取 [工具] > [延伸模組和更新]</span><span class="sxs-lookup"><span data-stu-id="c62b6-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 開啟延伸模組管理員對話方塊](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="c62b6-122">在 [延伸模組和更新] 提示內部，選取「線上」節點。</span><span class="sxs-lookup"><span data-stu-id="c62b6-122">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="c62b6-123">在搜尋列中，搜尋「ML.NET 模型建立器」，然後從結果中選取 ML.NET 模型建立器 (預覽)</span><span class="sxs-lookup"><span data-stu-id="c62b6-123">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![[擴充管理員] 對話方塊中的 VS2017 搜尋和安裝模型產生器擴充功能](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="c62b6-125">遵循提示完成安裝</span><span class="sxs-lookup"><span data-stu-id="c62b6-125">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="c62b6-126">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="c62b6-126">Visual Studio 2019</span></span>

1. <span data-ttu-id="c62b6-127">在功能表列上，選取 [延伸模組] > [管理延伸模組]</span><span class="sxs-lookup"><span data-stu-id="c62b6-127">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 開啟延伸模組管理員對話方塊](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="c62b6-129">在 [延伸模組和更新] 提示內部，選取「線上」節點。</span><span class="sxs-lookup"><span data-stu-id="c62b6-129">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="c62b6-130">在搜尋列中鍵入「ML.NET 模型建立器」，選取 ML.NET 模型建立器 (預覽)</span><span class="sxs-lookup"><span data-stu-id="c62b6-130">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![[擴充管理員] 對話方塊中的 VS2019 搜尋和安裝模型產生器擴充功能](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="c62b6-132">遵循提示完成安裝</span><span class="sxs-lookup"><span data-stu-id="c62b6-132">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="c62b6-133">解除安裝</span><span class="sxs-lookup"><span data-stu-id="c62b6-133">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="c62b6-134">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c62b6-134">Visual Studio 2017</span></span>

1. <span data-ttu-id="c62b6-135">在功能表列上，選取 [工具] > [延伸模組和更新]</span><span class="sxs-lookup"><span data-stu-id="c62b6-135">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 開啟管理延伸模組對話方塊](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="c62b6-137">在 [延伸模組和更新] 提示內部，展開「已安裝的」節點，然後選取 [工具]</span><span class="sxs-lookup"><span data-stu-id="c62b6-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="c62b6-138">從工具清單選取 ML.NET 模型建立器 (預覽)，然後選取 [解除安裝]</span><span class="sxs-lookup"><span data-stu-id="c62b6-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![[擴充管理員] 對話方塊中的 VS2017 搜尋和卸載模型產生器擴充功能](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="c62b6-140">遵循提示完成解除安裝。</span><span class="sxs-lookup"><span data-stu-id="c62b6-140">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="c62b6-141">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="c62b6-141">Visual Studio 2019</span></span>

1. <span data-ttu-id="c62b6-142">在功能表列上，選取 [延伸模組] > [管理延伸模組]</span><span class="sxs-lookup"><span data-stu-id="c62b6-142">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 開啟管理延伸模組對話方塊](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="c62b6-144">在 [延伸模組和更新] 提示內部，展開「已安裝的」節點，然後選取 [工具]</span><span class="sxs-lookup"><span data-stu-id="c62b6-144">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="c62b6-145">從工具清單選取 ML.NET 模型建立器 (預覽)，然後選取 [解除安裝]</span><span class="sxs-lookup"><span data-stu-id="c62b6-145">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![[擴充管理員] 對話方塊中的 VS2019 搜尋和卸載模型產生器擴充功能](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="c62b6-147">遵循提示完成解除安裝。</span><span class="sxs-lookup"><span data-stu-id="c62b6-147">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="c62b6-148">升級</span><span class="sxs-lookup"><span data-stu-id="c62b6-148">Upgrade</span></span>

<span data-ttu-id="c62b6-149">升級程序類似安裝程序。</span><span class="sxs-lookup"><span data-stu-id="c62b6-149">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="c62b6-150">從 Visual Studio Marketplace 或使用 Visual Studio 的延伸模組管理員下載最新版本。</span><span class="sxs-lookup"><span data-stu-id="c62b6-150">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
