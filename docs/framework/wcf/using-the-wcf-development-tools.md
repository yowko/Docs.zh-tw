---
title: 使用 WCF 開發工具
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 3eb349fd795b2067d4d75ff138fd9b5922110bd3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421276"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="e0182-102">使用 WCF 開發工具</span><span class="sxs-lookup"><span data-stu-id="e0182-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="e0182-103">本節說明可協助您開發 wcf 服務的 Visual Studio 開發工具。</span><span class="sxs-lookup"><span data-stu-id="e0182-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="e0182-104">您可以使用 Visual Studio 範本做為基礎，快速建置您自己的服務，然後使用 WCF 服務自動主機和 WCF 測試用戶端來偵錯和測試您的服務。</span><span class="sxs-lookup"><span data-stu-id="e0182-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="e0182-105">這些工具都提供了迅速完善的偵錯與測試循環，而且在早期階段不需要認可裝載模型。</span><span class="sxs-lookup"><span data-stu-id="e0182-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="e0182-106">WCF 開發者工具</span><span class="sxs-lookup"><span data-stu-id="e0182-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="e0182-107">WCF Visual Studio 範本</span><span class="sxs-lookup"><span data-stu-id="e0182-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="e0182-108">您可以使用 Visual Studio 中的預先定義的 Visual Studio 專案和項目範本，快速建置 WCF 服務和相關的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0182-108">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="e0182-109">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="e0182-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="e0182-110">WCF 服務自動主機 (WcfSvcHost.exe) 可讓您啟動 Visual Studio 偵錯工具 (F5) 來自動裝載並測試您已實作的服務。</span><span class="sxs-lookup"><span data-stu-id="e0182-110">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="e0182-111">然後，您可以測試使用 WCF 測試用戶端 (wcfTestClient.exe) 或您自己的用戶端來找出並修正任何潛在錯誤的服務。</span><span class="sxs-lookup"><span data-stu-id="e0182-111">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="e0182-112">WCF 測試用戶端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="e0182-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="e0182-113">WCF 測試用戶端 (WcfTestClient.exe) 是一種 GUI 工具，可讓您輸入任意型別的參數，將該服務，以及檢視服務的回應傳回輸入送出。</span><span class="sxs-lookup"><span data-stu-id="e0182-113">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="e0182-114">它提供了完善的服務測試經驗與 WCF 服務自動主機結合時。</span><span class="sxs-lookup"><span data-stu-id="e0182-114">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="e0182-115">從 XML 產生資料類型類別</span><span class="sxs-lookup"><span data-stu-id="e0182-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="e0182-116">儲存在剪貼簿中的 XML 資料可以貼到程式碼頁面上。</span><span class="sxs-lookup"><span data-stu-id="e0182-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="e0182-117">在資料中定義的類別將會轉換為程式碼型別。</span><span class="sxs-lookup"><span data-stu-id="e0182-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="e0182-118">在沒有系統管理員權限的情況下使用工具</span><span class="sxs-lookup"><span data-stu-id="e0182-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="e0182-119">若要啟用沒有系統管理員權限的使用者來開發 WCF 服務，ACL （存取控制清單） 建立命名空間"http://+:8731/Design_Time_Addresses"Visual Studio 安裝期間。</span><span class="sxs-lookup"><span data-stu-id="e0182-119">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="e0182-120">ACL 會設定為 (UI)，其中包含已登入電腦的所有互動使用者。</span><span class="sxs-lookup"><span data-stu-id="e0182-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="e0182-121">系統管理員可以在這個 ACL 中新增或移除使用者，或是開啟其他連接埠。這個 ACL 可讓 WCF 或 WF 範本傳送及接收其預設組態中的資料。</span><span class="sxs-lookup"><span data-stu-id="e0182-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="e0182-122">它也可讓使用者使用 WCF 服務自動主機 (wcfSvcHost.exe)，而不授與他們系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="e0182-122">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="e0182-123">您可以更高權限的系統管理員帳戶身分，使用 [!INCLUDE[wv](../../../includes/wv-md.md)] 中的 Netsh.exe 工具來修改存取權。</span><span class="sxs-lookup"><span data-stu-id="e0182-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="e0182-124">下列是使用 Netsh.exe 的範例。</span><span class="sxs-lookup"><span data-stu-id="e0182-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="e0182-125">如需 Netsh.exe 的詳細資訊，請參閱[如何使用 Netsh.exe 工具和命令列參數](https://go.microsoft.com/fwlink/?LinkId=97877)。</span><span class="sxs-lookup"><span data-stu-id="e0182-125">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](https://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0182-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0182-126">See Also</span></span>  
 [<span data-ttu-id="e0182-127">WCF Visual Studio 範本</span><span class="sxs-lookup"><span data-stu-id="e0182-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="e0182-128">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="e0182-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="e0182-129">WCF 測試用戶端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="e0182-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
