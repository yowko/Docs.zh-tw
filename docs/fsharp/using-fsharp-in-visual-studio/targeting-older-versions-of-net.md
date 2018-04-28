---
title: 以 Windows 8 上的 .NET Framework 2.0 為目標平台
description: '深入了解使用 F # 時，目標為舊版的.NET Framework。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 7c9bd8087da94a476105729b6f5b050fc66629a2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="targeting-older-versions-of-net"></a><span data-ttu-id="b9261-103">以舊版 .NET 為目標</span><span class="sxs-lookup"><span data-stu-id="b9261-103">Targeting Older Versions of .NET</span></span>

> [!NOTE]
<span data-ttu-id="b9261-104">這篇文章不是最新的 Visual Studio 中的最新狀態。</span><span class="sxs-lookup"><span data-stu-id="b9261-104">This article is not up to date with the latest Visual Studio.</span></span>  <span data-ttu-id="b9261-105">將會更新。</span><span class="sxs-lookup"><span data-stu-id="b9261-105">It will be updated.</span></span>

<span data-ttu-id="b9261-106">如果您嘗試將目標.NET Framework 2.0，3.0 或 3.5 F # 專案在 Windows 8.1 上安裝 Visual Studio 時，可能發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="b9261-106">The following error might appear if you try to target the .NET Framework 2.0, 3.0, or 3.5 in an F# project when Visual Studio is installed on Windows 8.1:</span></span> 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

<span data-ttu-id="b9261-107">這個錯誤是已知會發生在下列條件的組合：</span><span class="sxs-lookup"><span data-stu-id="b9261-107">This error is known to occur under the following combination of conditions:</span></span>


- <span data-ttu-id="b9261-108">您在 Windows 8.1 上安裝 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="b9261-108">You installed Visual Studio on Windows 8.1.</span></span>
<br />

- <span data-ttu-id="b9261-109">您未啟用.NET Framework 3.5，才能安裝 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="b9261-109">You didn’t enable the .NET Framework 3.5 before you installed Visual Studio.</span></span>
<br />

- <span data-ttu-id="b9261-110">您專案的目標.NET Framework 2.0、 3.0 或 3.5。</span><span class="sxs-lookup"><span data-stu-id="b9261-110">Your project targets the .NET Framework 2.0, 3.0, or 3.5.</span></span>
<br />

<span data-ttu-id="b9261-111">當您安裝 Visual Studio 時，它會偵測已安裝的.NET Framework 版本，並安裝並啟用.NET Framework 3.5 時，才會安裝 F # 2.0 執行階段。</span><span class="sxs-lookup"><span data-stu-id="b9261-111">When you install Visual Studio, it detects the installed versions of the .NET Framework and installs the F# 2.0 Runtime only if the .NET Framework 3.5 is installed and enabled.</span></span>


## <a name="resolving-the-error"></a><span data-ttu-id="b9261-112">解決錯誤</span><span class="sxs-lookup"><span data-stu-id="b9261-112">Resolving the Error</span></span>
<span data-ttu-id="b9261-113">若要解決這個錯誤，您可以任一目標較新版的.NET Framework 中，或者您可以啟用 Windows 8.1 上為.NET Framework 3.5，然後再安裝 F # 2.0 執行階段執行安裝程式的 Visual Studio 中以**修復**選項。</span><span class="sxs-lookup"><span data-stu-id="b9261-113">To resolve this error, you can either target a newer version of the .NET Framework, or you can enable the .NET Framework 3.5 on Windows 8.1 and then install the F# 2.0 runtime by running the setup program for Visual Studio with the **Repair** option.</span></span>


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a><span data-ttu-id="b9261-114">若要啟用 Windows 8.1 上為.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="b9261-114">To enable the .NET Framework 3.5 on Windows 8.1</span></span>

1. <span data-ttu-id="b9261-115">在**啟動**畫面上，開始輸入**控制台**。</span><span class="sxs-lookup"><span data-stu-id="b9261-115">On the **Start** screen, start to enter **Control Panel**.</span></span>
<br />  <span data-ttu-id="b9261-116">當您輸入該名稱，**控制台**圖示會出現在**應用程式**標題。</span><span class="sxs-lookup"><span data-stu-id="b9261-116">As you enter that name, the **Control Panel** icon appears under the **Apps** heading.</span></span>
<br />

2. <span data-ttu-id="b9261-117">選擇**控制台**圖示，選擇**程式**圖示，然後選擇 **開啟或關閉 Windows 功能**連結。</span><span class="sxs-lookup"><span data-stu-id="b9261-117">Choose the **Control Panel** icon, choose the **Programs** icon, and then choose the **Turn Windows features on or off** link.</span></span>
<br />

3. <span data-ttu-id="b9261-118">請確定 **.NET Framework 3.5 （包括.NET 2.0 和 3.0）**核取方塊已選取，然後選擇**確定** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b9261-118">Make sure that the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box is selected, and then choose the **OK** button.</span></span>
<br />  <span data-ttu-id="b9261-119">您不需要選取核取方塊，任何的子節點的.NET framework 的選擇性元件。</span><span class="sxs-lookup"><span data-stu-id="b9261-119">You don’t need to select the check boxes for any child nodes for optional components of the .NET Framework.</span></span>
<br />  <span data-ttu-id="b9261-120">如果尚未，啟用.NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="b9261-120">The .NET Framework 3.5 is enabled if it wasn't already.</span></span>
<br />


#### <a name="to-install-the-f-20-runtime"></a><span data-ttu-id="b9261-121">若要安裝 F # 2.0 執行階段</span><span class="sxs-lookup"><span data-stu-id="b9261-121">To install the F# 2.0 runtime</span></span>

1. <span data-ttu-id="b9261-122">在 控制台 中選擇**程式**連結，，然後選擇 **程式和功能**連結。</span><span class="sxs-lookup"><span data-stu-id="b9261-122">In the Control Panel, choose the **Programs** link, and then choose the **Programs and Features** link.</span></span>
<br />

2. <span data-ttu-id="b9261-123">在已安裝的程式清單中，選擇的版本，您已安裝，然後選擇 [Visual Studio**變更**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b9261-123">In the list of installed programs, choose the edition of Visual Studio that you installed, and then choose the **Change** button.</span></span>
<br />

3. <span data-ttu-id="b9261-124">安裝程式啟動之後，請選擇**修復** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b9261-124">After setup starts, choose the **Repair** button.</span></span>
<br />  <span data-ttu-id="b9261-125">如需詳細資訊，請參閱[安裝 Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b9261-125">For more information, see [Installing Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).</span></span>
<br />
## <a name="see-also"></a><span data-ttu-id="b9261-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9261-126">See Also</span></span>
[<span data-ttu-id="b9261-127">Visual F#</span><span class="sxs-lookup"><span data-stu-id="b9261-127">Visual F#</span></span>](../index.md)
