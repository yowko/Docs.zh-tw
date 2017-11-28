---
title: "每秒發生錯誤的呼叫數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e60ad3d7e9155eecfead38aca080a3044b0efce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="calls-faulted-per-second"></a><span data-ttu-id="f9212-102">每秒發生錯誤的呼叫數</span><span class="sxs-lookup"><span data-stu-id="f9212-102">Calls Faulted Per Second</span></span>
<span data-ttu-id="f9212-103">計數器名稱：每秒發生錯誤的呼叫數</span><span class="sxs-lookup"><span data-stu-id="f9212-103">Counter Name: Calls Faulted Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="f9212-104">描述</span><span class="sxs-lookup"><span data-stu-id="f9212-104">Description</span></span>  
 <span data-ttu-id="f9212-105">每秒將錯誤傳回至此作業的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="f9212-105">Number of calls that returned faults to this operation in a second.</span></span>  
  
 <span data-ttu-id="f9212-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="f9212-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f9212-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="f9212-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="f9212-108">在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 應用程式中，服務方法使用 SOAP 錯誤訊息來溝通處理錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="f9212-108">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="f9212-109">SOAP 錯誤是包含在服務作業之中繼資料內的訊息類型，因此會建立錯誤合約，而用戶端可使用該合約來讓其執行作業更強固或更具互動性。</span><span class="sxs-lookup"><span data-stu-id="f9212-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="f9212-110">由於 SOAP 錯誤會以 XML 表單的形式傳達給用戶端，所以其互通性很高。</span><span class="sxs-lookup"><span data-stu-id="f9212-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9212-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9212-111">See Also</span></span>  
 [<span data-ttu-id="f9212-112">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="f9212-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
