---
title: 端點：發生錯誤的呼叫數
ms.date: 03/30/2017
ms.assetid: 271e6284-9c4b-465f-b619-069e1555a5e4
ms.openlocfilehash: da8f771e93a9457944046dfe84a1a7a455388d77
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250121"
---
# <a name="endpoint-calls-faulted"></a><span data-ttu-id="0cfcc-102">端點：發生錯誤的呼叫數</span><span class="sxs-lookup"><span data-stu-id="0cfcc-102">Endpoint: Calls Faulted</span></span>

<span data-ttu-id="0cfcc-103">計數器名稱：發生錯誤的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0cfcc-104">描述</span><span class="sxs-lookup"><span data-stu-id="0cfcc-104">Description</span></span>  

 <span data-ttu-id="0cfcc-105">對這個端點有傳回錯誤的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-105">Number of calls to this endpoint that have returned faults.</span></span> <span data-ttu-id="0cfcc-106">在 Windows Communication Foundation (WCF) 應用程式中，服務方法會使用 SOAP 錯誤訊息來溝通處理錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-106">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="0cfcc-107">SOAP 錯誤是包含在服務作業之中繼資料內的訊息類型，因此會建立錯誤合約，而用戶端可使用該合約來讓其執行作業更強固或更具互動性。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="0cfcc-108">由於 SOAP 錯誤會以 XML 表單的形式傳達給用戶端，所以其互通性很高。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cfcc-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cfcc-109">See also</span></span>

- [<span data-ttu-id="0cfcc-110">指定與處理合約和服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="0cfcc-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
