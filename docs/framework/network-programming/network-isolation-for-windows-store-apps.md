---
title: "Windows 市集應用程式的網路隔離"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b6c0665a379f02a74bd0f3631aa26b41dd6ece5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="5f749-102">Windows 市集應用程式的網路隔離</span><span class="sxs-lookup"><span data-stu-id="5f749-102">Network Isolation for Windows Store Apps</span></span>
<span data-ttu-id="5f749-103"><xref:System.Net>、<xref:System.Net.Http> 和 <xref:System.Net.Http.Headers> 命名空間中的類別可以用來開發 Windows 市集應用程式或傳統型應用程式。</span><span class="sxs-lookup"><span data-stu-id="5f749-103">Classes in the <xref:System.Net>,  <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="5f749-104">在 Windows 市集應用程式中使用時，這些命名空間中的類別受到網路隔離的影響，而網路隔離是 [!INCLUDE[win8](../../../includes/win8-md.md)] 所使用應用程式安全性模型的一部分。</span><span class="sxs-lookup"><span data-stu-id="5f749-104">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by the [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span> <span data-ttu-id="5f749-105">必須在 Windows 市集應用程式的應用程式資訊清單中啟用適當的網路功能，讓系統允許網路存取。</span><span class="sxs-lookup"><span data-stu-id="5f749-105">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="5f749-106">網路隔離的檢查清單</span><span class="sxs-lookup"><span data-stu-id="5f749-106">Checklist for Network Isolation</span></span>  
 <span data-ttu-id="5f749-107">使用此檢查清單，確定已設定 Windows 市集應用程式的網路隔離。</span><span class="sxs-lookup"><span data-stu-id="5f749-107">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1.  <span data-ttu-id="5f749-108">決定應用程式所需的網路存取要求方向。</span><span class="sxs-lookup"><span data-stu-id="5f749-108">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="5f749-109">這可以是輸出用戶端起始的要求或輸入未經要求的要求，或是這兩種網路要求類型的組合。</span><span class="sxs-lookup"><span data-stu-id="5f749-109">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2.  <span data-ttu-id="5f749-110">判斷該應用程式將與其通訊的網路資源類型。</span><span class="sxs-lookup"><span data-stu-id="5f749-110">Determine the type of network resources that that app will communicate with.</span></span> <span data-ttu-id="5f749-111">應用程式可能需要與家用或工作場所網路上受信任的資源進行通訊。</span><span class="sxs-lookup"><span data-stu-id="5f749-111">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="5f749-112">應用程式可能需要與網際網路上的資源進行通訊。</span><span class="sxs-lookup"><span data-stu-id="5f749-112">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="5f749-113">應用程式可能需要存取這兩種類型的網路資源。</span><span class="sxs-lookup"><span data-stu-id="5f749-113">An app might need access to both types of network resources.</span></span>  
  
3.  <span data-ttu-id="5f749-114">在應用程式資訊清單中設定最低必要網路隔離功能。</span><span class="sxs-lookup"><span data-stu-id="5f749-114">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4.  <span data-ttu-id="5f749-115">部署和執行應用程式，以使用針對疑難排解所提供的網路隔離工具對其進行測試。</span><span class="sxs-lookup"><span data-stu-id="5f749-115">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
 <span data-ttu-id="5f749-116">如需如何設定用於針對網路隔離進行疑難排解之網路功能和隔離工具的詳細資訊，請參閱 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 開發人員文件中的[如何設定網路隔離功能](http://go.microsoft.com/fwlink/?LinkID=228265)。</span><span class="sxs-lookup"><span data-stu-id="5f749-116">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](http://go.microsoft.com/fwlink/?LinkID=228265) in the [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] developer documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f749-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f749-117">See Also</span></span>  
 [<span data-ttu-id="5f749-118">連接到 web 服務</span><span class="sxs-lookup"><span data-stu-id="5f749-118">Connecting to a web service</span></span>](http://go.microsoft.com/fwlink/?LinkID=245696)  
 [<span data-ttu-id="5f749-119">方針和網路隔離的檢查清單</span><span class="sxs-lookup"><span data-stu-id="5f749-119">Guidelines and checklist for network isolation</span></span>](http://go.microsoft.com/fwlink/?LinkID=228265)  
 [<span data-ttu-id="5f749-120">快速入門： 使用 HttpClient 來連接</span><span class="sxs-lookup"><span data-stu-id="5f749-120">Quickstart: Connecting using HttpClient</span></span>](http://go.microsoft.com/fwlink/?LinkId=245697)  
 [<span data-ttu-id="5f749-121">如何使用 HttpClient 處理常式</span><span class="sxs-lookup"><span data-stu-id="5f749-121">How to use HttpClient handlers</span></span>](http://go.microsoft.com/fwlink/?LinkId=245699)  
 [<span data-ttu-id="5f749-122">如何保護 HttpClient 連線</span><span class="sxs-lookup"><span data-stu-id="5f749-122">How to secure HttpClient connections</span></span>](http://go.microsoft.com/fwlink/?LinkId=245698)  
 [<span data-ttu-id="5f749-123">HttpClient 範例</span><span class="sxs-lookup"><span data-stu-id="5f749-123">HttpClient Sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=242550)
