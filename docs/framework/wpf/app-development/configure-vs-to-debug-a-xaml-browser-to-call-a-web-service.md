---
title: 作法：設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: e41dd46e4ddbdcde6448c68b4f9fb2e073baca43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958692"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="3871f-102">作法：設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務</span><span class="sxs-lookup"><span data-stu-id="3871f-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]<span data-ttu-id="3871f-103">在限制為網際網路區域許可權集的部分信任安全性沙箱中執行。</span><span class="sxs-lookup"><span data-stu-id="3871f-103">run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="3871f-104">這個許可權集合會將 web 服務通話限制為位於[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]應用程式來源網站上的 web 服務。</span><span class="sxs-lookup"><span data-stu-id="3871f-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="3871f-105">不過, 從 Visual Studio 2005進行調試時,不會將它所參考的Web服務視為相同的來源網站。[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3871f-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="3871f-106">這會導致在[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]嘗試呼叫 Web 服務時引發安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3871f-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="3871f-107">不過, Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]專案可以設定為模擬與在進行調試時所呼叫的 Web 服務相同的來源網站。</span><span class="sxs-lookup"><span data-stu-id="3871f-107">However, a Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="3871f-108">這可讓[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]安全地呼叫 Web 服務, 而不會導致安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3871f-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="3871f-109">設定 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3871f-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="3871f-110">若要將 Visual Studio 2005 設定為[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]可偵測呼叫 Web 服務的:</span><span class="sxs-lookup"><span data-stu-id="3871f-110">To configure Visual Studio 2005 to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>

1. <span data-ttu-id="3871f-111">在方案總管中選取專案之後，按一下 [專案] 功能表中 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="3871f-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="3871f-112">在 [**專案設計**工具] 中, 按一下 [**調試**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3871f-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="3871f-113">在 [**起始動作**] 區段中, 選取 [**啟動外部程式**], 並輸入下列內容:</span><span class="sxs-lookup"><span data-stu-id="3871f-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="3871f-114">在 [**開始選項**] 區段的 [**命令列引數**] 文字方塊中, 輸入下列內容:</span><span class="sxs-lookup"><span data-stu-id="3871f-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="3871f-115">`-debug`  *名稱*</span><span class="sxs-lookup"><span data-stu-id="3871f-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="3871f-116">**-Debug**參數的*檔案名*值是 xbap filename;例如:</span><span class="sxs-lookup"><span data-stu-id="3871f-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
> <span data-ttu-id="3871f-117">這是使用 Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]專案範本所建立之解決方案的預設設定。</span><span class="sxs-lookup"><span data-stu-id="3871f-117">This is the default configuration for solutions that are created with the Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>

1. <span data-ttu-id="3871f-118">在方案總管中選取專案之後，按一下 [專案] 功能表中 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="3871f-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="3871f-119">在 [**專案設計**工具] 中, 按一下 [**調試**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3871f-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="3871f-120">在 [**啟動選項**] 區段中, 將下列命令列參數新增至 [**命令列引數**] 文字方塊:</span><span class="sxs-lookup"><span data-stu-id="3871f-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="3871f-121">`-debugSecurityZoneURL`  *URL*</span><span class="sxs-lookup"><span data-stu-id="3871f-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="3871f-122">**-DebugSecurityZoneURL** [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)]參數的*URL*值是您想要模擬為應用程式來源網站的位置。</span><span class="sxs-lookup"><span data-stu-id="3871f-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="3871f-123">例如, 請考慮[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]使用 Web 服務的, 其具有下列[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]各項:</span><span class="sxs-lookup"><span data-stu-id="3871f-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="3871f-124">此 Web 服務的[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]來源網站為:</span><span class="sxs-lookup"><span data-stu-id="3871f-124">The site of origin [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="3871f-125">因此, 完整的**debugSecurityZoneURL**命令列參數和值為:</span><span class="sxs-lookup"><span data-stu-id="3871f-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="3871f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3871f-126">See also</span></span>

- [<span data-ttu-id="3871f-127">WPF 主應用程式 (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="3871f-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)
