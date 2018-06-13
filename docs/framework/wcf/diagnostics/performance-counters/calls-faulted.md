---
title: 發生錯誤的呼叫數
ms.date: 03/30/2017
ms.assetid: bb9e8045-6aeb-4b7f-a825-8283c44252a1
ms.openlocfilehash: 26d79d74980d0bab93acace29bc24df7b473c4f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472741"
---
# <a name="calls-faulted"></a><span data-ttu-id="186b5-102">發生錯誤的呼叫數</span><span class="sxs-lookup"><span data-stu-id="186b5-102">Calls Faulted</span></span>
<span data-ttu-id="186b5-103">計數器名稱：發生錯誤的呼叫數</span><span class="sxs-lookup"><span data-stu-id="186b5-103">Counter Name: Calls Faulted</span></span>  
  
## <a name="description"></a><span data-ttu-id="186b5-104">描述</span><span class="sxs-lookup"><span data-stu-id="186b5-104">Description</span></span>  
 <span data-ttu-id="186b5-105">傳回錯誤之這個作業的呼叫次數。</span><span class="sxs-lookup"><span data-stu-id="186b5-105">Number of calls to this operation that returned faults.</span></span> <span data-ttu-id="186b5-106">Windows Communication Foundation (WCF) 應用程式中，服務方法通訊使用 SOAP 錯誤訊息的處理錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="186b5-106">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="186b5-107">SOAP 錯誤是包含在服務作業之中繼資料內的訊息類型，因此會建立錯誤合約，而用戶端可使用該合約來讓其執行作業更強固或更具互動性。</span><span class="sxs-lookup"><span data-stu-id="186b5-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="186b5-108">由於 SOAP 錯誤會以 XML 表單的形式傳達給用戶端，所以其互通性很高。</span><span class="sxs-lookup"><span data-stu-id="186b5-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="186b5-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="186b5-109">See Also</span></span>  
 [<span data-ttu-id="186b5-110">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="186b5-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
