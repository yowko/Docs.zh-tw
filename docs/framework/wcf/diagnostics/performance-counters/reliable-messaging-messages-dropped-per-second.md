---
title: 每秒捨棄的可信賴傳訊訊息數
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 946e0408b8b6602bba7824b45e4d6cb91cdaa4eb
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163952"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="2ab0d-102">每秒捨棄的可信賴傳訊訊息數</span><span class="sxs-lookup"><span data-stu-id="2ab0d-102">Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="2ab0d-103">計數器名稱：每秒捨棄的可信賴傳訊工作階段數。</span><span class="sxs-lookup"><span data-stu-id="2ab0d-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2ab0d-104">描述</span><span class="sxs-lookup"><span data-stu-id="2ab0d-104">Description</span></span>  
 <span data-ttu-id="2ab0d-105">在此服務中已捨棄的每秒可信賴傳訊訊息總數。</span><span class="sxs-lookup"><span data-stu-id="2ab0d-105">Total number of reliable messaging messages that have been dropped in this service in a second.</span></span>  
  
 <span data-ttu-id="2ab0d-106">此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="2ab0d-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2ab0d-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="2ab0d-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
