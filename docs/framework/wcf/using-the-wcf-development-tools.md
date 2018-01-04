---
title: "使用 WCF 開發工具"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d253f38fab21496dd305cc67e7b6e84846579f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="04986-102">使用 WCF 開發工具</span><span class="sxs-lookup"><span data-stu-id="04986-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="04986-103">本章節描述[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)][!INCLUDE[indigo1](../../../includes/indigo1-md.md)]開發工具，可協助您開發程式[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="04986-103">This section describes the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)][!INCLUDE[indigo1](../../../includes/indigo1-md.md)] development tools that can assist you in developing your [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]service.</span></span>  
  
 <span data-ttu-id="04986-104">您可以使用[!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]範本做為基礎，快速建立您自己的服務，然後使用[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務自動主機和[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]測試用戶端來偵錯和測試您的服務。</span><span class="sxs-lookup"><span data-stu-id="04986-104">You can use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] templates as a foundation to quickly build your own service, then use [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host and [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client to debug and test your service.</span></span> <span data-ttu-id="04986-105">這些工具都提供了迅速完善的偵錯與測試循環，而且在早期階段不需要認可裝載模型。</span><span class="sxs-lookup"><span data-stu-id="04986-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="04986-106">WCF 開發者工具</span><span class="sxs-lookup"><span data-stu-id="04986-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="04986-107">WCF Visual Studio 範本</span><span class="sxs-lookup"><span data-stu-id="04986-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="04986-108">您可以使用預先定義[!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]中的專案和項目範本[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]快速建置[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務和相關的應用程式。</span><span class="sxs-lookup"><span data-stu-id="04986-108">You can use the predefined [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] project and item templates in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] to quickly build [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="04986-109">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="04986-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="04986-110">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務自動裝載 (WcfSvcHost.exe) 可讓您啟動 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 偵錯工具 (F5) 來自動裝載並測試您已實作的服務。</span><span class="sxs-lookup"><span data-stu-id="04986-110">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (WcfSvcHost.exe) allows you to launch the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="04986-111">然後，您可以使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 測試用戶端 (wcfTestClient.exe) 或自己的用戶端來測試服務，以尋找並修正任何可能的錯誤。</span><span class="sxs-lookup"><span data-stu-id="04986-111">You can then test the service using the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="04986-112">WCF 測試用戶端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="04986-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="04986-113"> 測試用戶端 (WcfTestClient.exe) 是一種 GUI 工具，可讓您輸入任意型別的參數、將該輸入送出至服務，以及檢視服務傳回的回應。</span><span class="sxs-lookup"><span data-stu-id="04986-113"> Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="04986-114">與 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務自動主機相結合時，這個用戶端也提供了完善的服務測試經驗。</span><span class="sxs-lookup"><span data-stu-id="04986-114">It provides a seamless service testing experience when combined with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host.</span></span>  
  
 [<span data-ttu-id="04986-115">從 XML 產生資料類型類別</span><span class="sxs-lookup"><span data-stu-id="04986-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="04986-116">儲存在剪貼簿中的 XML 資料可以貼到程式碼頁面上。</span><span class="sxs-lookup"><span data-stu-id="04986-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="04986-117">在資料中定義的類別將會轉換為程式碼型別。</span><span class="sxs-lookup"><span data-stu-id="04986-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="04986-118">在沒有系統管理員權限的情況下使用工具</span><span class="sxs-lookup"><span data-stu-id="04986-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="04986-119">為了讓沒有系統管理員權限的使用者能夠開發 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務，在安裝 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 期間會建立命名空間 "http://+:8731/Design_Time_Addresses" 的 ACL (存取控制清單)。</span><span class="sxs-lookup"><span data-stu-id="04986-119">To enable users without administrator privilege to develop [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="04986-120">ACL 會設定為 (UI)，其中包含已登入電腦的所有互動使用者。</span><span class="sxs-lookup"><span data-stu-id="04986-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="04986-121">系統管理員可以在這個 ACL 中新增或移除使用者，或是開啟其他連接埠。這個 ACL 可讓 WCF 或 WF 範本傳送及接收其預設組態中的資料。</span><span class="sxs-lookup"><span data-stu-id="04986-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="04986-122">也可以讓使用者在未取得系統管理員權限的情況下使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務自動主機 (wcfSvcHost.exe)。</span><span class="sxs-lookup"><span data-stu-id="04986-122">It also enables users to use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="04986-123">您可以更高權限的系統管理員帳戶身分，使用 [!INCLUDE[wv](../../../includes/wv-md.md)] 中的 Netsh.exe 工具來修改存取權。</span><span class="sxs-lookup"><span data-stu-id="04986-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="04986-124">下列是使用 Netsh.exe 的範例。</span><span class="sxs-lookup"><span data-stu-id="04986-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="04986-125">Netsh.exe，請參閱[如何使用 Netsh.exe 工具和命令列參數](http://go.microsoft.com/fwlink/?LinkId=97877)。</span><span class="sxs-lookup"><span data-stu-id="04986-125"> Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](http://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04986-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="04986-126">See Also</span></span>  
 [<span data-ttu-id="04986-127">WCF Visual Studio 範本</span><span class="sxs-lookup"><span data-stu-id="04986-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="04986-128">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="04986-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="04986-129">WCF 測試用戶端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="04986-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
