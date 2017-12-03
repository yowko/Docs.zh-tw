---
title: "服務：發生錯誤的呼叫數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: daae4da05e2c1d68147f23256d868a6124479417
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="service-calls-faulted"></a><span data-ttu-id="04d04-102">服務：發生錯誤的呼叫數</span><span class="sxs-lookup"><span data-stu-id="04d04-102">Service: Calls Faulted</span></span>
<span data-ttu-id="04d04-103">計數器名稱：發生錯誤的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="04d04-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="04d04-104">描述</span><span class="sxs-lookup"><span data-stu-id="04d04-104">Description</span></span>  
 <span data-ttu-id="04d04-105">針對已傳回錯誤之此服務的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="04d04-105">Number of calls to this service that have returned faults.</span></span> <span data-ttu-id="04d04-106">在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 應用程式中，服務方法使用 SOAP 錯誤訊息來溝通處理錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="04d04-106">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="04d04-107">SOAP 錯誤是包含在服務作業之中繼資料內的訊息類型，因此會建立錯誤合約，而用戶端可使用該合約來讓其執行作業更強固或更具互動性。</span><span class="sxs-lookup"><span data-stu-id="04d04-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="04d04-108">由於 SOAP 錯誤會以 XML 表單的形式傳達給用戶端，所以其互通性很高。</span><span class="sxs-lookup"><span data-stu-id="04d04-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d04-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04d04-109">See Also</span></span>  
 [<span data-ttu-id="04d04-110">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="04d04-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
