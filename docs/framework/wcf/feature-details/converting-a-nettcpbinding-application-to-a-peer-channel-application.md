---
title: "將 NetTcpBinding 應用程式轉換為對等通道應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ee46e34aea14c4ee9ce23c807170104173f2704
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="1fa49-102">將 NetTcpBinding 應用程式轉換為對等通道應用程式</span><span class="sxs-lookup"><span data-stu-id="1fa49-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="1fa49-103">您可以使用會描述連線參數的繫結，在使用 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 的用戶端之間建立連線。</span><span class="sxs-lookup"><span data-stu-id="1fa49-103">You can create connections between clients using the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="1fa49-104">轉換 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 應用程式以使用對等連線時，會需要在進行用戶端連線時支援此技術的繫結。</span><span class="sxs-lookup"><span data-stu-id="1fa49-104">Converting a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="1fa49-105">對等通道會提供名稱為 <xref:System.ServiceModel.NetPeerTcpBinding> 的繫結，其使用方法類似於使用 <xref:System.ServiceModel.NetTcpBinding>。</span><span class="sxs-lookup"><span data-stu-id="1fa49-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="1fa49-106">之間的主要差異則包括指定解析程式服務和定義安全性設定。</span><span class="sxs-lookup"><span data-stu-id="1fa49-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="1fa49-107">如果應用程式使用預設解析程式和安全性設定，轉換正常用戶端/伺服器型應用程式以使用對等通道則牽涉到在應用程式的組態檔中將繫結的名稱從 "NetTcpBinding" 變更為 "NetPeerTcpBinding"，而您並不需要變更應用程式的程式碼基礎。</span><span class="sxs-lookup"><span data-stu-id="1fa49-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fa49-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="1fa49-108">See Also</span></span>  
 [<span data-ttu-id="1fa49-109">建置對等通道應用程式</span><span class="sxs-lookup"><span data-stu-id="1fa49-109">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)  
 [<span data-ttu-id="1fa49-110">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="1fa49-110">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
