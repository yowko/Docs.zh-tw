---
title: Windows 市集應用程式的網路隔離
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 0f9288b53b969838cac64c24d3c9861a0f841aca
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558455"
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="8d275-102">Windows 市集應用程式的網路隔離</span><span class="sxs-lookup"><span data-stu-id="8d275-102">Network Isolation for Windows Store Apps</span></span>

<span data-ttu-id="8d275-103"><xref:System.Net>、 <xref:System.Net.Http> 和命名空間中的類別 <xref:System.Net.Http.Headers> 可以用來開發 Windows Store 應用程式或桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d275-103">Classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="8d275-104">在 Windows Store 應用程式中使用時，這些命名空間中的類別會受到網路隔離的影響，也就是 Windows 8 使用的應用程式安全性模型的一部分。</span><span class="sxs-lookup"><span data-stu-id="8d275-104">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by Windows 8.</span></span> <span data-ttu-id="8d275-105">必須在 Windows 市集應用程式的應用程式資訊清單中啟用適當的網路功能，讓系統允許網路存取。</span><span class="sxs-lookup"><span data-stu-id="8d275-105">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="8d275-106">網路隔離的檢查清單</span><span class="sxs-lookup"><span data-stu-id="8d275-106">Checklist for Network Isolation</span></span>  

<span data-ttu-id="8d275-107">使用此檢查清單，確定已設定 Windows 市集應用程式的網路隔離。</span><span class="sxs-lookup"><span data-stu-id="8d275-107">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1. <span data-ttu-id="8d275-108">決定應用程式所需的網路存取要求方向。</span><span class="sxs-lookup"><span data-stu-id="8d275-108">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="8d275-109">這可以是輸出用戶端起始的要求或輸入未經要求的要求，或是這兩種網路要求類型的組合。</span><span class="sxs-lookup"><span data-stu-id="8d275-109">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2. <span data-ttu-id="8d275-110">判斷該應用程式將與其通訊的網路資源類型。</span><span class="sxs-lookup"><span data-stu-id="8d275-110">Determine the type of network resources that the app will communicate with.</span></span> <span data-ttu-id="8d275-111">應用程式可能需要與家用或工作場所網路上受信任的資源進行通訊。</span><span class="sxs-lookup"><span data-stu-id="8d275-111">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="8d275-112">應用程式可能需要與網際網路上的資源進行通訊。</span><span class="sxs-lookup"><span data-stu-id="8d275-112">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="8d275-113">應用程式可能需要存取這兩種類型的網路資源。</span><span class="sxs-lookup"><span data-stu-id="8d275-113">An app might need access to both types of network resources.</span></span>  
  
3. <span data-ttu-id="8d275-114">在應用程式資訊清單中設定最低必要網路隔離功能。</span><span class="sxs-lookup"><span data-stu-id="8d275-114">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4. <span data-ttu-id="8d275-115">部署和執行應用程式，以使用針對疑難排解所提供的網路隔離工具對其進行測試。</span><span class="sxs-lookup"><span data-stu-id="8d275-115">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
<span data-ttu-id="8d275-116">如需有關如何設定網路功能的詳細資訊，以及用於疑難排解網路隔離的隔離工具，請參閱 Windows 8. x 存放區開發人員檔中的 [如何設定網路隔離功能](/previous-versions/windows/apps/hh770532(v=win.10)) 。</span><span class="sxs-lookup"><span data-stu-id="8d275-116">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](/previous-versions/windows/apps/hh770532(v=win.10)) in the Windows 8.x Store developer documentation.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8d275-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d275-117">See also</span></span>

- <span data-ttu-id="8d275-118">[連線至 Web 服務](/previous-versions/windows/apps/hh761504(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="8d275-118">[Connecting to a web service](/previous-versions/windows/apps/hh761504(v=win.10))</span></span>
- <span data-ttu-id="8d275-119">[網路隔離的方針和檢查清單](/previous-versions/windows/apps/hh770532(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="8d275-119">[Guidelines and checklist for network isolation](/previous-versions/windows/apps/hh770532(v=win.10))</span></span>
- <span data-ttu-id="8d275-120">[快速入門：使用 HttpClient 進行連線](/previous-versions/windows/apps/hh781239(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="8d275-120">[Quickstart: Connecting using HttpClient](/previous-versions/windows/apps/hh781239(v=win.10))</span></span>
- <span data-ttu-id="8d275-121">[如何使用 HttpClient 處理常式](/previous-versions/windows/apps/hh781241(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="8d275-121">[How to use HttpClient handlers](/previous-versions/windows/apps/hh781241(v=win.10))</span></span>
- <span data-ttu-id="8d275-122">[如何保護 HttpClient 連線](/previous-versions/windows/apps/hh781240(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="8d275-122">[How to secure HttpClient connections](/previous-versions/windows/apps/hh781240(v=win.10))</span></span>
- [<span data-ttu-id="8d275-123">HttpClient 範例</span><span class="sxs-lookup"><span data-stu-id="8d275-123">HttpClient Sample</span></span>](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
