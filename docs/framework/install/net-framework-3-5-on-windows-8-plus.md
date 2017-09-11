---
title: "在 Windows 8、Windows 8.1 和 Windows 10 上安裝 .NET Framework 3.5"
ms.date: 05/26/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework 3.5, installing on Windows 8
- Windows 8, installing .NET Framework 3.5
ms.assetid: 3eab3eb4-4573-42ac-98f8-36fb2c22c7d5
caps.latest.revision: 69
author: mairaw
ms.author: mairaw
ms.translationtype: HT
ms.sourcegitcommit: 93f77dd5c3ca61935ae98ddef15f9c5cf7644bbb
ms.openlocfilehash: e9c8dcfacff689761d9ec891db8a1a4756acece0
ms.contentlocale: zh-tw
ms.lasthandoff: 08/23/2017

---

# <a name="install-the-net-framework-35-on-windows-8-windows-81-and-windows-10"></a><span data-ttu-id="f9f07-102">在 Windows 8、Windows 8.1 和 Windows 10 上安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="f9f07-102">Install the .NET Framework 3.5 on Windows 8, Windows 8.1, and Windows 10</span></span>

<span data-ttu-id="f9f07-103">.NET Framework 是在 Windows 上執行之許多應用程式不可或缺的一部分，提供應用程式執行所需的常見功能。</span><span class="sxs-lookup"><span data-stu-id="f9f07-103">The .NET Framework is an integral part of many apps running on Windows and provides common functionality for those apps to run.</span></span> <span data-ttu-id="f9f07-104">對於開發人員而言，.NET Framework 提供一個一致的程式設計模型，以便建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9f07-104">For developers, the .NET Framework provides a consistent programming model for building apps.</span></span> <span data-ttu-id="f9f07-105">如果您使用的是 Windows 作業系統，您的電腦上可能已經安裝了 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="f9f07-105">If you're using the Windows operating system, the .NET Framework may already be installed on your computer.</span></span> <span data-ttu-id="f9f07-106">具體來說，[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 會隨附於 [!INCLUDE[win8](../../../includes/win8-md.md)]、[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 會隨附於 [!INCLUDE[win81](../../../includes/win81-md.md)]，而 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 會隨附於 Windows 10。</span><span class="sxs-lookup"><span data-stu-id="f9f07-106">Specifically, the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is included with [!INCLUDE[win8](../../../includes/win8-md.md)], the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] is included with [!INCLUDE[win81](../../../includes/win81-md.md)], and the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] is included with Windows 10.</span></span>  
  
<span data-ttu-id="f9f07-107">不過，.NET Framework 3.5 不會隨 [!INCLUDE[win8](../../../includes/win8-md.md)]、[!INCLUDE[win81](../../../includes/win81-md.md)] 或 Windows 10 自動安裝，而必須個別啟用才能執行與其相依的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9f07-107">The .NET Framework 3.5, however, is not automatically installed with [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], or Windows 10, and must be separately enabled to run apps that depend on it.</span></span> <span data-ttu-id="f9f07-108">這必須透過 Windows Update (可使用三種方法的其中一種來呼叫) 進行。</span><span class="sxs-lookup"><span data-stu-id="f9f07-108">This must happen through Windows Update, which is invoked in one of three ways.</span></span> <span data-ttu-id="f9f07-109">所有這些項目都需要網際網路連線：</span><span class="sxs-lookup"><span data-stu-id="f9f07-109">All of these require an Internet connection:</span></span>  
  
- [<span data-ttu-id="f9f07-110">視需要安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="f9f07-110">Install the .NET Framework 3.5 on Demand</span></span>](#OnDemand)  
  
- [<span data-ttu-id="f9f07-111">在控制台中啟用 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="f9f07-111">Enable the .NET Framework 3.5 in Control Panel</span></span>](#ControlPanel)  
  
- <span data-ttu-id="f9f07-112">[下載 .NET Framework 3.5 安裝程式](http://www.microsoft.com/en-us/download/details.aspx?id=21) (注意：這不會直接下載 .NET Framework；它是叫用 Windows Update 的安裝程式)。</span><span class="sxs-lookup"><span data-stu-id="f9f07-112">[Download the .NET Framework 3.5 installer](http://www.microsoft.com/en-us/download/details.aspx?id=21) (Note: This does not download the .NET Framework directly; it is an installer that invokes Windows Update.)</span></span>  
  
<span data-ttu-id="f9f07-113">在安裝過程中，您可能會遇到錯誤 0x800f0906、0x800f0907 或 0x800f081f，如果發生這種情況，請參考 [.NET Framework 3.5 安裝錯誤：0x800f0906、0x800f0907 或 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09)。</span><span class="sxs-lookup"><span data-stu-id="f9f07-113">During installation, you may encounter error 0x800f0906, 0x800f0907, or 0x800f081f, in which case refer to [.NET Framework 3.5 installation error: 0x800f0906, 0x800f0907, or 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09).</span></span> <span data-ttu-id="f9f07-114">請注意，安裝 [安全性更新 3005628](https://support.microsoft.com/kb/3005628)可能會解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="f9f07-114">Note that these are possibly resolved by installing [security update 3005628](https://support.microsoft.com/kb/3005628).</span></span>  
  
<span data-ttu-id="f9f07-115">如果上述任何方法失敗，或者您沒有網際網路連線，則必須使用 Windows 安裝媒體。</span><span class="sxs-lookup"><span data-stu-id="f9f07-115">If any of the above methods fail or if you do not have an Internet connection, it's necessary to use your Windows installation media.</span></span> <span data-ttu-id="f9f07-116">如需詳細資訊，請參閱 [.NET Framework 3.5 安裝錯誤文章](https://support.microsoft.com/en-us/kb/2734782)中錯誤 0x800f0906 的方法 3。</span><span class="sxs-lookup"><span data-stu-id="f9f07-116">For details, see Method 3 for error 0x800f0906 in the [.NET Framework 3.5 installation error article](https://support.microsoft.com/en-us/kb/2734782).</span></span> <span data-ttu-id="f9f07-117">如果您沒有安裝媒體，請參閱[建立 Windows 8.1 的安裝媒體](http://windows.microsoft.com/en-US/windows-8/create-reset-refresh-media?woldogcb=0)。</span><span class="sxs-lookup"><span data-stu-id="f9f07-117">If you don't have installation media, see [Create Installation media for Windows 8.1](http://windows.microsoft.com/en-US/windows-8/create-reset-refresh-media?woldogcb=0).</span></span>  
  
<span data-ttu-id="f9f07-118">**重要注意事項：**</span><span class="sxs-lookup"><span data-stu-id="f9f07-118">**Important notes:**</span></span>
  
- <span data-ttu-id="f9f07-119">一般而言，請勿解除安裝電腦上的任何 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="f9f07-119">In general, don't uninstall any versions of the .NET Framework from your computer.</span></span> <span data-ttu-id="f9f07-120">不同的應用程式相依於不同版本的 Framework，而一部電腦上可同時並存多種 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="f9f07-120">Different apps depend on different versions of the framework, and multiple versions of the .NET Framework can coexist on a single computer at the same time.</span></span>  
  
- <span data-ttu-id="f9f07-121">針對 2.0 和 3.0 版建置的應用程式也會使用 .NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="f9f07-121">The .NET Framework 3.5 is also used by apps built for versions 2.0 and 3.0.</span></span>  
  
- <span data-ttu-id="f9f07-122">在安裝 .NET Framework 3.5 之前安裝 Windows 語言套件，可能會導致 .NET Framework 3.5 安裝失敗。</span><span class="sxs-lookup"><span data-stu-id="f9f07-122">Installing a Windows language pack before installing the .NET Framework 3.5 may cause the .NET Framework 3.5 installation to fail.</span></span> <span data-ttu-id="f9f07-123">在安裝任何 Windows 語言套件之前，請先安裝 .NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="f9f07-123">Install the .NET Framework 3.5 before installing any Windows language packs.</span></span>  
  
- <span data-ttu-id="f9f07-124">Windows CardSpace 無法在 [!INCLUDE[win8](../../../includes/win8-md.md)]上搭配 .NET Framework 3.5 使用。</span><span class="sxs-lookup"><span data-stu-id="f9f07-124">Windows CardSpace is not available with the .NET Framework 3.5 on [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span>  
  
- <span data-ttu-id="f9f07-125">由於 .NET Framework 3.5 安裝方式的複雜性，因而無法提供可與 Windows Update 分開執行的個別獨立安裝程式。</span><span class="sxs-lookup"><span data-stu-id="f9f07-125">Because of complications around how the .NET Framework 3.5 must be installed, it's unfortunately not possible to provide a separate, standalone installer that can run independently of Windows Update.</span></span> <span data-ttu-id="f9f07-126">如果所有其他方法都失敗，就必須求助於安裝媒體 (如前所述)。</span><span class="sxs-lookup"><span data-stu-id="f9f07-126">If all other methods fail, you must resort to installation media as described earlier.</span></span>  
  
<a name="OnDemand"></a>   
## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="f9f07-127">視需要安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="f9f07-127">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="f9f07-128">如果應用程式需要 .NET Framework 3.5，但電腦上找不到已啟用的這個版本，則會在安裝期間或您第一次執行應用程式時顯示下列訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="f9f07-128">If an app requires the .NET Framework 3.5 but doesn't find that version enabled on your computer, it displays the following message box, either during installation or when you run the app for the first time.</span></span> <span data-ttu-id="f9f07-129">在訊息方塊中，選擇 [ **安裝此功能** ] 啟用 .NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="f9f07-129">In the message box, choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="f9f07-130">這個選項需要網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="f9f07-130">This option requires an Internet connection.</span></span>  
  
<span data-ttu-id="f9f07-131">![在 Windows 8 上安裝 3.5 時顯示的對話方塊](../../../docs/framework/deployment/media/installdialog.png "installdialog")</span><span class="sxs-lookup"><span data-stu-id="f9f07-131">![Dialog box for 3.5 install on Windows 8](../../../docs/framework/deployment/media/installdialog.png "installdialog")</span></span>  
  
<a name="ControlPanel"></a>   
## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="f9f07-132">在控制台中啟用 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="f9f07-132">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="f9f07-133">您可以透過 [控制台] 啟用 .NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="f9f07-133">You can enable the .NET Framework 3.5 through Control Panel.</span></span> <span data-ttu-id="f9f07-134">這個選項需要網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="f9f07-134">This option requires an Internet connection.</span></span>  
  
1. <span data-ttu-id="f9f07-135">按下鍵盤上的 Windows 鍵 ![Windows 標誌](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")。</span><span class="sxs-lookup"><span data-stu-id="f9f07-135">Press the Windows key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard.</span></span> <span data-ttu-id="f9f07-136">鍵入「Windows 功能」，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="f9f07-136">Type "Windows Features" and press Enter.</span></span> <span data-ttu-id="f9f07-137">這會開啟 [開啟或關閉 Windows 功能]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f9f07-137">This brings up the **Turn Windows features on or off** dialog box.</span></span> <span data-ttu-id="f9f07-138">或者，開啟 [控制台]，按一下 [程式] 項目，然後選取 [程式和功能] 下的 [開啟或關閉 Windows 功能]。</span><span class="sxs-lookup"><span data-stu-id="f9f07-138">Alternately, open Control Panel, click on the **Programs** items, and then select **Turn Windows features on or off** under **Programs and Features**.</span></span>  
  
2. <span data-ttu-id="f9f07-139">選取 [.NET Framework 3.5 (包括 .NET 2.0 和 3.0)] 核取方塊，選取 [確定]，然後在出現提示時重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="f9f07-139">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>  
  
<span data-ttu-id="f9f07-140">除非您是需要 WCF 指令碼和處理常式對應功能的開發人員，否則不需要選取 **Windows Communication Foundation (WCF) HTTP 啟用**的子項目。</span><span class="sxs-lookup"><span data-stu-id="f9f07-140">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP activation** unless you're a developer who requires WCF script and handler mapping functionality.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f9f07-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="f9f07-141">See also</span></span>

[<span data-ttu-id="f9f07-142">安裝指南</span><span class="sxs-lookup"><span data-stu-id="f9f07-142">Installation Guide</span></span>](../../../docs/framework/get-started/index.md)

