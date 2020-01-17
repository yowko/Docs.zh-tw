---
title: 端點：每秒發生錯誤的可信賴傳訊工作階段數
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: 26fd8236af6516716f7cf9c7c06f669473bdfc3a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163185"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="fd347-102">端點：每秒發生錯誤的可信賴傳訊工作階段數</span><span class="sxs-lookup"><span data-stu-id="fd347-102">Endpoint: Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="fd347-103">計數器名稱：每秒發生錯誤的可信賴傳訊工作階段數。</span><span class="sxs-lookup"><span data-stu-id="fd347-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fd347-104">描述</span><span class="sxs-lookup"><span data-stu-id="fd347-104">Description</span></span>  
 <span data-ttu-id="fd347-105">在此端點每秒發生的可信賴傳訊工作階段錯誤數。</span><span class="sxs-lookup"><span data-stu-id="fd347-105">Number of reliable messaging sessions that are faulted at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="fd347-106">此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="fd347-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fd347-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="fd347-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
