---
title: 端點：每秒發生錯誤的呼叫數
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: 3b5c881c4ce7772e197bfc1a5603636b0975143c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517652"
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="cefe2-102">端點：每秒發生錯誤的呼叫數</span><span class="sxs-lookup"><span data-stu-id="cefe2-102">Endpoint: Calls Faulted Per Second</span></span>
<span data-ttu-id="cefe2-103">計數器名稱：每秒發生錯誤的呼叫。</span><span class="sxs-lookup"><span data-stu-id="cefe2-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cefe2-104">描述</span><span class="sxs-lookup"><span data-stu-id="cefe2-104">Description</span></span>  
 <span data-ttu-id="cefe2-105">每秒傳回至此端點的錯誤呼叫數。</span><span class="sxs-lookup"><span data-stu-id="cefe2-105">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="cefe2-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="cefe2-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="cefe2-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="cefe2-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="cefe2-108">在 Windows Communication Foundation (WCF) 應用程式，服務方法通訊，使用 SOAP 錯誤訊息的處理錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="cefe2-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="cefe2-109">SOAP 錯誤是包含在服務作業之中繼資料內的訊息類型，因此會建立錯誤合約，而用戶端可使用該合約來讓其執行作業更強固或更具互動性。</span><span class="sxs-lookup"><span data-stu-id="cefe2-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="cefe2-110">由於 SOAP 錯誤會以 XML 表單的形式傳達給用戶端，所以其互通性很高。</span><span class="sxs-lookup"><span data-stu-id="cefe2-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cefe2-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cefe2-111">See also</span></span>
- [<span data-ttu-id="cefe2-112">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="cefe2-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
