---
title: 使用 WCF 開發工具
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7e315c9e77eace9bdb0e66abed203452e5d7f9bb
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="4fa93-102">使用 WCF 開發工具</span><span class="sxs-lookup"><span data-stu-id="4fa93-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="4fa93-103">本節描述可協助您開發的 Visual Studio 開發工具程式[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="4fa93-103">This section describes the Visual Studio development tools that can assist you in developing your [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]service.</span></span>  
  
 <span data-ttu-id="4fa93-104">您可以使用 Visual Studio 範本為基礎來快速建立您自己的服務，請使用[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務自動主機和[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]測試用戶端來偵錯和測試您的服務。</span><span class="sxs-lookup"><span data-stu-id="4fa93-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host and [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client to debug and test your service.</span></span> <span data-ttu-id="4fa93-105">這些工具都提供了迅速完善的偵錯與測試循環，而且在早期階段不需要認可裝載模型。</span><span class="sxs-lookup"><span data-stu-id="4fa93-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="4fa93-106">WCF 開發者工具</span><span class="sxs-lookup"><span data-stu-id="4fa93-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="4fa93-107">WCF Visual Studio 範本</span><span class="sxs-lookup"><span data-stu-id="4fa93-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="4fa93-108">您可以在 Visual Studio 中使用預先定義的 Visual Studio 專案和項目範本快速建置[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務和相關的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4fa93-108">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="4fa93-109">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="4fa93-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="4fa93-110">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務自動主機 (WcfSvcHost.exe) 可讓您啟動 Visual Studio 偵錯工具 (F5) 來自動裝載並測試您已實作的服務。</span><span class="sxs-lookup"><span data-stu-id="4fa93-110">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="4fa93-111">然後，您可以使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 測試用戶端 (wcfTestClient.exe) 或自己的用戶端來測試服務，以尋找並修正任何可能的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4fa93-111">You can then test the service using the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="4fa93-112">WCF 測試用戶端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="4fa93-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="4fa93-113"> 測試用戶端 (WcfTestClient.exe) 是一種 GUI 工具，可讓您輸入任意型別的參數、將該輸入送出至服務，以及檢視服務傳回的回應。</span><span class="sxs-lookup"><span data-stu-id="4fa93-113"> Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="4fa93-114">與 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務自動主機相結合時，這個用戶端也提供了完善的服務測試經驗。</span><span class="sxs-lookup"><span data-stu-id="4fa93-114">It provides a seamless service testing experience when combined with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host.</span></span>  
  
 [<span data-ttu-id="4fa93-115">從 XML 產生資料類型類別</span><span class="sxs-lookup"><span data-stu-id="4fa93-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="4fa93-116">儲存在剪貼簿中的 XML 資料可以貼到程式碼頁面上。</span><span class="sxs-lookup"><span data-stu-id="4fa93-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="4fa93-117">在資料中定義的類別將會轉換為程式碼型別。</span><span class="sxs-lookup"><span data-stu-id="4fa93-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="4fa93-118">在沒有系統管理員權限的情況下使用工具</span><span class="sxs-lookup"><span data-stu-id="4fa93-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="4fa93-119">為了讓沒有系統管理員權限來開發使用者[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]，ACL （存取控制清單） 建立服務命名空間"http://+:8731/Design_Time_Addresses"Visual Studio 安裝期間。</span><span class="sxs-lookup"><span data-stu-id="4fa93-119">To enable users without administrator privilege to develop [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="4fa93-120">ACL 會設定為 (UI)，其中包含已登入電腦的所有互動使用者。</span><span class="sxs-lookup"><span data-stu-id="4fa93-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="4fa93-121">系統管理員可以在這個 ACL 中新增或移除使用者，或是開啟其他連接埠。這個 ACL 可讓 WCF 或 WF 範本傳送及接收其預設組態中的資料。</span><span class="sxs-lookup"><span data-stu-id="4fa93-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="4fa93-122">也可以讓使用者在未取得系統管理員權限的情況下使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務自動主機 (wcfSvcHost.exe)。</span><span class="sxs-lookup"><span data-stu-id="4fa93-122">It also enables users to use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="4fa93-123">您可以更高權限的系統管理員帳戶身分，使用 [!INCLUDE[wv](../../../includes/wv-md.md)] 中的 Netsh.exe 工具來修改存取權。</span><span class="sxs-lookup"><span data-stu-id="4fa93-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="4fa93-124">下列是使用 Netsh.exe 的範例。</span><span class="sxs-lookup"><span data-stu-id="4fa93-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="4fa93-125"> Netsh.exe，請參閱[如何使用 Netsh.exe 工具和命令列參數](http://go.microsoft.com/fwlink/?LinkId=97877)。</span><span class="sxs-lookup"><span data-stu-id="4fa93-125"> Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](http://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa93-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fa93-126">See Also</span></span>  
 [<span data-ttu-id="4fa93-127">WCF Visual Studio 範本</span><span class="sxs-lookup"><span data-stu-id="4fa93-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="4fa93-128">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="4fa93-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="4fa93-129">WCF 測試用戶端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="4fa93-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
