---
title: "以 Windows 8 上的 .NET Framework 2.0 為目標平台"
description: "深入了解使用 F # 時，目標為舊版的.NET Framework。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63989543-95c3-4ab7-81f3-3834a8b15010
ms.openlocfilehash: 2c0191267da5bee7b844c11cdee168ccfb3321c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="targeting-older-versions-of-net"></a><span data-ttu-id="793fa-104">以舊版 .NET 為目標</span><span class="sxs-lookup"><span data-stu-id="793fa-104">Targeting Older Versions of .NET</span></span>

> [!NOTE]
<span data-ttu-id="793fa-105">這篇文章不是最新的 Visual Studio 中的最新狀態。</span><span class="sxs-lookup"><span data-stu-id="793fa-105">This article is not up to date with the latest Visual Studio.</span></span>  <span data-ttu-id="793fa-106">將會更新。</span><span class="sxs-lookup"><span data-stu-id="793fa-106">It will be updated.</span></span>

<span data-ttu-id="793fa-107">如果您嘗試將目標.NET Framework 2.0，3.0 或 3.5 F # 專案在 Windows 8.1 上安裝 Visual Studio 時，可能發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="793fa-107">The following error might appear if you try to target the .NET Framework 2.0, 3.0, or 3.5 in an F# project when Visual Studio is installed on Windows 8.1:</span></span> 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

<span data-ttu-id="793fa-108">這個錯誤是已知會發生在下列條件的組合：</span><span class="sxs-lookup"><span data-stu-id="793fa-108">This error is known to occur under the following combination of conditions:</span></span>


- <span data-ttu-id="793fa-109">您在 Windows 8.1 上安裝 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="793fa-109">You installed Visual Studio on Windows 8.1.</span></span>
<br />

- <span data-ttu-id="793fa-110">您未啟用.NET Framework 3.5，才能安裝 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="793fa-110">You didn’t enable the .NET Framework 3.5 before you installed Visual Studio.</span></span>
<br />

- <span data-ttu-id="793fa-111">您專案的目標.NET Framework 2.0、 3.0 或 3.5。</span><span class="sxs-lookup"><span data-stu-id="793fa-111">Your project targets the .NET Framework 2.0, 3.0, or 3.5.</span></span>
<br />

<span data-ttu-id="793fa-112">當您安裝 Visual Studio 時，它會偵測已安裝的.NET Framework 版本，並安裝並啟用.NET Framework 3.5 時，才會安裝 F # 2.0 執行階段。</span><span class="sxs-lookup"><span data-stu-id="793fa-112">When you install Visual Studio, it detects the installed versions of the .NET Framework and installs the F# 2.0 Runtime only if the .NET Framework 3.5 is installed and enabled.</span></span>


## <a name="resolving-the-error"></a><span data-ttu-id="793fa-113">解決錯誤</span><span class="sxs-lookup"><span data-stu-id="793fa-113">Resolving the Error</span></span>
<span data-ttu-id="793fa-114">若要解決這個錯誤，您可以任一目標較新版的.NET Framework 中，或者您可以啟用 Windows 8.1 上為.NET Framework 3.5，然後再安裝 F # 2.0 執行階段執行安裝程式的 Visual Studio 中以**修復**選項。</span><span class="sxs-lookup"><span data-stu-id="793fa-114">To resolve this error, you can either target a newer version of the .NET Framework, or you can enable the .NET Framework 3.5 on Windows 8.1 and then install the F# 2.0 runtime by running the setup program for Visual Studio with the **Repair** option.</span></span>


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a><span data-ttu-id="793fa-115">若要啟用 Windows 8.1 上為.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="793fa-115">To enable the .NET Framework 3.5 on Windows 8.1</span></span>

1. <span data-ttu-id="793fa-116">在**啟動**畫面上，開始輸入**控制台**。</span><span class="sxs-lookup"><span data-stu-id="793fa-116">On the **Start** screen, start to enter **Control Panel**.</span></span>
<br />  <span data-ttu-id="793fa-117">當您輸入該名稱，**控制台**圖示會出現在**應用程式**標題。</span><span class="sxs-lookup"><span data-stu-id="793fa-117">As you enter that name, the **Control Panel** icon appears under the **Apps** heading.</span></span>
<br />

2. <span data-ttu-id="793fa-118">選擇**控制台**圖示，選擇**程式**圖示，然後選擇 **開啟或關閉 Windows 功能**連結。</span><span class="sxs-lookup"><span data-stu-id="793fa-118">Choose the **Control Panel** icon, choose the **Programs** icon, and then choose the **Turn Windows features on or off** link.</span></span>
<br />

3. <span data-ttu-id="793fa-119">請確定**.NET Framework 3.5 （包括.NET 2.0 和 3.0）**核取方塊已選取，然後選擇**確定** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="793fa-119">Make sure that the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box is selected, and then choose the **OK** button.</span></span>
<br />  <span data-ttu-id="793fa-120">您不需要選取核取方塊，任何的子節點的.NET framework 的選擇性元件。</span><span class="sxs-lookup"><span data-stu-id="793fa-120">You don’t need to select the check boxes for any child nodes for optional components of the .NET Framework.</span></span>
<br />  <span data-ttu-id="793fa-121">如果尚未，啟用.NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="793fa-121">The .NET Framework 3.5 is enabled if it wasn't already.</span></span>
<br />


#### <a name="to-install-the-f-20-runtime"></a><span data-ttu-id="793fa-122">若要安裝 F # 2.0 執行階段</span><span class="sxs-lookup"><span data-stu-id="793fa-122">To install the F# 2.0 runtime</span></span>

1. <span data-ttu-id="793fa-123">在 控制台 中選擇**程式**連結，，然後選擇 **程式和功能**連結。</span><span class="sxs-lookup"><span data-stu-id="793fa-123">In the Control Panel, choose the **Programs** link, and then choose the **Programs and Features** link.</span></span>
<br />

2. <span data-ttu-id="793fa-124">在已安裝的程式清單中，選擇的版本，您已安裝，然後選擇 [Visual Studio**變更**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="793fa-124">In the list of installed programs, choose the edition of Visual Studio that you installed, and then choose the **Change** button.</span></span>
<br />

3. <span data-ttu-id="793fa-125">安裝程式啟動之後，請選擇**修復** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="793fa-125">After setup starts, choose the **Repair** button.</span></span>
<br />  <span data-ttu-id="793fa-126">如需詳細資訊，請參閱[安裝 Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)。</span><span class="sxs-lookup"><span data-stu-id="793fa-126">For more information, see [Installing Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).</span></span>
<br />
## <a name="see-also"></a><span data-ttu-id="793fa-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="793fa-127">See Also</span></span>
[<span data-ttu-id="793fa-128">Visual F#</span><span class="sxs-lookup"><span data-stu-id="793fa-128">Visual F#</span></span>](../index.md)
