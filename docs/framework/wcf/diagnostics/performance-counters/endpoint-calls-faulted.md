---
title: "端點：發生錯誤的呼叫數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271e6284-9c4b-465f-b619-069e1555a5e4
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0997050887721f4b72eb2a69f41be966936b25c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-calls-faulted"></a><span data-ttu-id="122a8-102">端點：發生錯誤的呼叫數</span><span class="sxs-lookup"><span data-stu-id="122a8-102">Endpoint: Calls Faulted</span></span>
<span data-ttu-id="122a8-103">計數器名稱：發生錯誤的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="122a8-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="122a8-104">描述</span><span class="sxs-lookup"><span data-stu-id="122a8-104">Description</span></span>  
 <span data-ttu-id="122a8-105">對這個端點有傳回錯誤的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="122a8-105">Number of calls to this endpoint that have returned faults.</span></span> <span data-ttu-id="122a8-106">在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 應用程式中，服務方法使用 SOAP 錯誤訊息來溝通處理錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="122a8-106">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="122a8-107">SOAP 錯誤是包含在服務作業之中繼資料內的訊息類型，因此會建立錯誤合約，而用戶端可使用該合約來讓其執行作業更強固或更具互動性。</span><span class="sxs-lookup"><span data-stu-id="122a8-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="122a8-108">由於 SOAP 錯誤會以 XML 表單的形式傳達給用戶端，所以其互通性很高。</span><span class="sxs-lookup"><span data-stu-id="122a8-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="122a8-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="122a8-109">See Also</span></span>  
 [<span data-ttu-id="122a8-110">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="122a8-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
