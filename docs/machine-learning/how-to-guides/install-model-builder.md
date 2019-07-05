---
title: 如何安裝模型建立器
description: 了解如何安裝 ML.NET 模型建立器工具
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: 54ab595c56f816517180aab48022c7df207fe84d
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410566"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="fbf18-103">了解如何安裝 ML.NET 模型建立器</span><span class="sxs-lookup"><span data-stu-id="fbf18-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="fbf18-104">了解如何安裝 ML.NET 模型建立器，將機器學習服務新增至您的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fbf18-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="fbf18-105">模型建立器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="fbf18-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="fbf18-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="fbf18-106">Pre-requisites</span></span>

- <span data-ttu-id="fbf18-107">Visual Studio 2017 15.9.12 或更新版本 / Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="fbf18-107">Visual Studio 2017 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="fbf18-108">.NET Core 2.1 或更新版本的 SDK</span><span class="sxs-lookup"><span data-stu-id="fbf18-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="fbf18-109">限制</span><span class="sxs-lookup"><span data-stu-id="fbf18-109">Limitations</span></span>

- <span data-ttu-id="fbf18-110">ML.NET 模型建立器延伸模組目前僅適用於 Windows 的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="fbf18-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="fbf18-111">1 GB 的定型資料集限制</span><span class="sxs-lookup"><span data-stu-id="fbf18-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="fbf18-112">SQL Server 的定型上限為 10 萬筆資料列</span><span class="sxs-lookup"><span data-stu-id="fbf18-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="fbf18-113">不支援 Microsoft SQL Server Data Tools for Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fbf18-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="fbf18-114">安裝</span><span class="sxs-lookup"><span data-stu-id="fbf18-114">Install</span></span>

<span data-ttu-id="fbf18-115">您可透過 Visual Studio Marketplace，或從 Visual Studio 安裝 ML.NET 模型建立器。</span><span class="sxs-lookup"><span data-stu-id="fbf18-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span> 

### <a name="visual-studio-marketplace"></a><span data-ttu-id="fbf18-116">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="fbf18-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="fbf18-117">從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07) 下載</span><span class="sxs-lookup"><span data-stu-id="fbf18-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="fbf18-118">遵循提示安裝到個別的 Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="fbf18-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="fbf18-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fbf18-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="fbf18-120">在功能表列上，選取 [工具]   > [延伸模組和更新] </span><span class="sxs-lookup"><span data-stu-id="fbf18-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>
1. <span data-ttu-id="fbf18-121">在 [延伸模組和更新]  提示內部，選取「線上」  節點。</span><span class="sxs-lookup"><span data-stu-id="fbf18-121">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="fbf18-122">在搜尋列中，搜尋「ML.NET 模型建立器」  ，然後從結果中選取 ML.NET 模型建立器 (預覽)</span><span class="sxs-lookup"><span data-stu-id="fbf18-122">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>
1. <span data-ttu-id="fbf18-123">遵循提示完成安裝</span><span class="sxs-lookup"><span data-stu-id="fbf18-123">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="fbf18-124">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="fbf18-124">Visual Studio 2019</span></span>

1. <span data-ttu-id="fbf18-125">在功能表列上，選取 [延伸模組]   > [管理延伸模組] </span><span class="sxs-lookup"><span data-stu-id="fbf18-125">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>
1. <span data-ttu-id="fbf18-126">在 [延伸模組和更新]  提示內部，選取「線上」  節點。</span><span class="sxs-lookup"><span data-stu-id="fbf18-126">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="fbf18-127">在搜尋列中鍵入「ML.NET 模型建立器」  ，選取 ML.NET 模型建立器 (預覽)</span><span class="sxs-lookup"><span data-stu-id="fbf18-127">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>
1. <span data-ttu-id="fbf18-128">遵循提示完成安裝</span><span class="sxs-lookup"><span data-stu-id="fbf18-128">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="fbf18-129">解除安裝</span><span class="sxs-lookup"><span data-stu-id="fbf18-129">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="fbf18-130">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fbf18-130">Visual Studio 2017</span></span>

1. <span data-ttu-id="fbf18-131">在功能表列上，選取 [工具]   > [延伸模組和更新] </span><span class="sxs-lookup"><span data-stu-id="fbf18-131">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>
1. <span data-ttu-id="fbf18-132">在 [延伸模組和更新]  提示內部，展開「已安裝的」  節點，然後選取 [工具] </span><span class="sxs-lookup"><span data-stu-id="fbf18-132">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="fbf18-133">從工具清單選取 ML.NET 模型建立器 (預覽)，然後選取 [解除安裝] </span><span class="sxs-lookup"><span data-stu-id="fbf18-133">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>
1. <span data-ttu-id="fbf18-134">遵循提示完成解除安裝。</span><span class="sxs-lookup"><span data-stu-id="fbf18-134">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="fbf18-135">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="fbf18-135">Visual Studio 2019</span></span>

1. <span data-ttu-id="fbf18-136">在功能表列上，選取 [延伸模組]   > [管理延伸模組] </span><span class="sxs-lookup"><span data-stu-id="fbf18-136">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>
1. <span data-ttu-id="fbf18-137">在 [延伸模組和更新]  提示內部，展開「已安裝的」  節點，然後選取 [工具] </span><span class="sxs-lookup"><span data-stu-id="fbf18-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="fbf18-138">從工具清單選取 ML.NET 模型建立器 (預覽)，然後選取 [解除安裝] </span><span class="sxs-lookup"><span data-stu-id="fbf18-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>
1. <span data-ttu-id="fbf18-139">遵循提示完成解除安裝。</span><span class="sxs-lookup"><span data-stu-id="fbf18-139">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="fbf18-140">升級</span><span class="sxs-lookup"><span data-stu-id="fbf18-140">Upgrade</span></span>

<span data-ttu-id="fbf18-141">升級程序類似安裝程序。</span><span class="sxs-lookup"><span data-stu-id="fbf18-141">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="fbf18-142">從 Visual Studio Marketplace 或使用 Visual Studio 的延伸模組管理員下載最新版本。</span><span class="sxs-lookup"><span data-stu-id="fbf18-142">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
