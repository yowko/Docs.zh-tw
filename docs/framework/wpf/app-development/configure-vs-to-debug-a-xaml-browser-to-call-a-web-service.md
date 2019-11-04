---
title: 如何：設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: 27319179a9a30c5693f47039bf1e24c59adf0e68
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424660"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="285ed-102">如何：設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務</span><span class="sxs-lookup"><span data-stu-id="285ed-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
<span data-ttu-id="285ed-103">XAML 瀏覽器應用程式（Xbap）會在部分信任的安全性沙箱中執行，而此沙箱僅限於許可權的網際網路區域集。</span><span class="sxs-lookup"><span data-stu-id="285ed-103">XAML browser applications (XBAPs) run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="285ed-104">這個許可權集合會將 Web 服務通話限制為位於 XBAP 應用程式的來源網站上的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="285ed-104">This permission set restricts Web service calls to only Web services that are located at the XBAP application's site of origin.</span></span> <span data-ttu-id="285ed-105">不過，從 Visual Studio 2005 調試 XBAP 時，不會將其所參考之 Web 服務的來源網站視為相同。</span><span class="sxs-lookup"><span data-stu-id="285ed-105">When an XBAP is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="285ed-106">這會導致當 XBAP 嘗試呼叫 Web 服務時，會引發安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="285ed-106">This causes security exceptions to be raised when the XBAP attempts to call the Web service.</span></span> <span data-ttu-id="285ed-107">不過，Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] 專案可以設定為模擬與在進行調試時所呼叫的 Web 服務相同的來源網站。</span><span class="sxs-lookup"><span data-stu-id="285ed-107">However, a Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="285ed-108">這可讓 XBAP 安全地呼叫 Web 服務，而不會導致安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="285ed-108">This allows the XBAP to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="285ed-109">設定 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="285ed-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="285ed-110">若要將 Visual Studio 2005 設定為可偵測呼叫 Web 服務的 XBAP：</span><span class="sxs-lookup"><span data-stu-id="285ed-110">To configure Visual Studio 2005 to debug an XBAP that calls a Web service:</span></span>

1. <span data-ttu-id="285ed-111">在方案總管中選取專案之後，按一下 [專案] 功能表中 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="285ed-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="285ed-112">在 [**專案設計**工具] 中，按一下 [**調試**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="285ed-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="285ed-113">在 [**起始動作**] 區段中，選取 [**啟動外部程式**]，並輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="285ed-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="285ed-114">在 [**開始選項**] 區段的 [**命令列引數**] 文字方塊中，輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="285ed-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="285ed-115">`-debug`  *檔案名*</span><span class="sxs-lookup"><span data-stu-id="285ed-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="285ed-116">**-Debug**參數的*檔案名*值是 xbap filename;例如：</span><span class="sxs-lookup"><span data-stu-id="285ed-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
> <span data-ttu-id="285ed-117">這是使用 Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] 專案範本所建立之解決方案的預設設定。</span><span class="sxs-lookup"><span data-stu-id="285ed-117">This is the default configuration for solutions that are created with the Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>

1. <span data-ttu-id="285ed-118">在方案總管中選取專案之後，按一下 [專案] 功能表中 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="285ed-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="285ed-119">在 [**專案設計**工具] 中，按一下 [**調試**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="285ed-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="285ed-120">在 [**啟動選項**] 區段中，將下列命令列參數新增至 [**命令列引數**] 文字方塊：</span><span class="sxs-lookup"><span data-stu-id="285ed-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="285ed-121">`-debugSecurityZoneURL`  *URL*</span><span class="sxs-lookup"><span data-stu-id="285ed-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="285ed-122">**-DebugSecurityZoneURL**參數的*url*值是您想要模擬為應用程式來源網站之位置的 url。</span><span class="sxs-lookup"><span data-stu-id="285ed-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the URL for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="285ed-123">例如，假設 XAML 瀏覽器應用程式（XBAP）使用具有下列 URL 的 Web 服務：</span><span class="sxs-lookup"><span data-stu-id="285ed-123">As an example, consider a XAML browser application (XBAP) that uses a Web service with the following URL:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="285ed-124">此 Web 服務的來源網站 URL 為：</span><span class="sxs-lookup"><span data-stu-id="285ed-124">The site of origin URL for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="285ed-125">因此，完整的**debugSecurityZoneURL**命令列參數和值為：</span><span class="sxs-lookup"><span data-stu-id="285ed-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="285ed-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="285ed-126">See also</span></span>

- [<span data-ttu-id="285ed-127">WPF 主應用程式 (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="285ed-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)
