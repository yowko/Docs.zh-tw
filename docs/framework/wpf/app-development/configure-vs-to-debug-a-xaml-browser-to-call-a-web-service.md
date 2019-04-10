---
title: HOW TO：設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: dcaabf9ecd47bc88095e92aa8ed28ad5f13fd1dc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314369"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="1503d-102">HOW TO：設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務</span><span class="sxs-lookup"><span data-stu-id="1503d-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] <span data-ttu-id="1503d-103">網際網路區域集合的權限僅限於在部分信任安全性沙箱內執行。</span><span class="sxs-lookup"><span data-stu-id="1503d-103">run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="1503d-104">此權限集合會限制只有 web 服務，是位在 Web 服務呼叫[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]應用程式的來源網站。</span><span class="sxs-lookup"><span data-stu-id="1503d-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="1503d-105">當[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]進行偵錯從 Visual Studio 2005，不過，它不是擁有相同來源網站上的 Web 服務的方法參考。</span><span class="sxs-lookup"><span data-stu-id="1503d-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="1503d-106">此會導致安全性例外狀況，當引發[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]嘗試呼叫 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="1503d-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="1503d-107">不過，Visual Studio 2005[!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]專案可以設定為模擬擁有為其偵錯時所呼叫的 Web 服務相同的來源站台。</span><span class="sxs-lookup"><span data-stu-id="1503d-107">However, a Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="1503d-108">這可讓[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]來安全地呼叫 Web 服務，而不會造成安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1503d-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="1503d-109">設定 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1503d-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="1503d-110">若要設定 Visual Studio 2005 偵錯[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]呼叫 Web 服務：</span><span class="sxs-lookup"><span data-stu-id="1503d-110">To configure Visual Studio 2005 to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>

1. <span data-ttu-id="1503d-111">在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。</span><span class="sxs-lookup"><span data-stu-id="1503d-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="1503d-112">在 [**專案設計工具**，按一下**偵錯**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1503d-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="1503d-113">在 **起始動作**區段中，選取**啟動外部程式**並輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="1503d-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="1503d-114">在 **啟動選項**區段中，輸入下列內容輸入**命令列引數**文字方塊：</span><span class="sxs-lookup"><span data-stu-id="1503d-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     `-debug`  *<span data-ttu-id="1503d-115">filename</span><span class="sxs-lookup"><span data-stu-id="1503d-115">filename</span></span>*

     <span data-ttu-id="1503d-116">*檔名*值 **-偵錯**參數是.xbap 檔案名稱; 例如：</span><span class="sxs-lookup"><span data-stu-id="1503d-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
>  <span data-ttu-id="1503d-117">這是由 Visual Studio 2005 所建立之解決方案的預設組態[!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]專案範本。</span><span class="sxs-lookup"><span data-stu-id="1503d-117">This is the default configuration for solutions that are created with the Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>

1. <span data-ttu-id="1503d-118">在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。</span><span class="sxs-lookup"><span data-stu-id="1503d-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="1503d-119">在 [**專案設計工具**，按一下**偵錯**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1503d-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="1503d-120">在 **啟動選項**區段中，加入下列的命令列參數來**命令列引數**文字方塊：</span><span class="sxs-lookup"><span data-stu-id="1503d-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     `-debugSecurityZoneURL`  *<span data-ttu-id="1503d-121">URL</span><span class="sxs-lookup"><span data-stu-id="1503d-121">URL</span></span>*

     <span data-ttu-id="1503d-122">*URL*值 **-debugSecurityZoneURL**參數是[!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)]您想要模擬為您的應用程式的來源網站上的位置。</span><span class="sxs-lookup"><span data-stu-id="1503d-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="1503d-123">例如，請考慮[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]使用 Web 服務以下列[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="1503d-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="1503d-124">來源網站上的[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]為此 Web 服務是：</span><span class="sxs-lookup"><span data-stu-id="1503d-124">The site of origin [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="1503d-125">因此，完整 **-debugSecurityZoneURL**命令列參數，而且值是：</span><span class="sxs-lookup"><span data-stu-id="1503d-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="1503d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1503d-126">See also</span></span>

- [<span data-ttu-id="1503d-127">WPF 主應用程式 (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="1503d-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)
