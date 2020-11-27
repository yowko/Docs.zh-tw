---
title: 服務：每秒發生錯誤的呼叫數
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: d9db777d17de51caff74610d099a79228df1f6d8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252942"
---
# <a name="service-calls-faulted-per-second"></a><span data-ttu-id="9fbf6-102">服務：每秒發生錯誤的呼叫數</span><span class="sxs-lookup"><span data-stu-id="9fbf6-102">Service: Calls Faulted Per Second</span></span>

<span data-ttu-id="9fbf6-103">計數器名稱：每秒發生錯誤的呼叫數</span><span class="sxs-lookup"><span data-stu-id="9fbf6-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9fbf6-104">描述</span><span class="sxs-lookup"><span data-stu-id="9fbf6-104">Description</span></span>  

 <span data-ttu-id="9fbf6-105">每秒傳回至此服務的錯誤呼叫數。</span><span class="sxs-lookup"><span data-stu-id="9fbf6-105">Number of calls that have returned faults to this service in a second.</span></span>  
  
 <span data-ttu-id="9fbf6-106">此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="9fbf6-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9fbf6-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="9fbf6-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="9fbf6-108">在 Windows Communication Foundation (WCF) 應用程式中，服務方法會使用 SOAP 錯誤訊息來溝通處理錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="9fbf6-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="9fbf6-109">SOAP 錯誤是包含在服務作業之中繼資料內的訊息類型，因此會建立錯誤合約，而用戶端可使用該合約來讓其執行作業更強固或更具互動性。</span><span class="sxs-lookup"><span data-stu-id="9fbf6-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="9fbf6-110">由於 SOAP 錯誤會以 XML 表單的形式傳達給用戶端，所以其互通性很高。</span><span class="sxs-lookup"><span data-stu-id="9fbf6-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fbf6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fbf6-111">See also</span></span>

- [<span data-ttu-id="9fbf6-112">指定與處理合約和服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="9fbf6-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
