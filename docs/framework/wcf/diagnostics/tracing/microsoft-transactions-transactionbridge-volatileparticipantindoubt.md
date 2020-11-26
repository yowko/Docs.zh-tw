---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: 9ad9dc9fd078f7ad4c0934c8bf9bb73feb935014
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236646"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="051c5-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="051c5-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>

<span data-ttu-id="051c5-103">WS-AT 通訊協定服務已收到「已準備」或「重新執行」訊息，但均來自無法辨識的變動參與者。</span><span class="sxs-lookup"><span data-stu-id="051c5-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="051c5-104">錯誤已傳回給參與者，宣告異動結果不確定。</span><span class="sxs-lookup"><span data-stu-id="051c5-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="051c5-105">描述</span><span class="sxs-lookup"><span data-stu-id="051c5-105">Description</span></span>  

 <span data-ttu-id="051c5-106">在本機異動管理員收到來自其已忘記的變動登記之「已準備」或「重新執行」訊息時追蹤。</span><span class="sxs-lookup"><span data-stu-id="051c5-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="051c5-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="051c5-107">Troubleshooting</span></span>  

 <span data-ttu-id="051c5-108">調查來自變動參與者的晚期訊息潛在原因。</span><span class="sxs-lookup"><span data-stu-id="051c5-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="051c5-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="051c5-109">See also</span></span>

- [<span data-ttu-id="051c5-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="051c5-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="051c5-111">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="051c5-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="051c5-112">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="051c5-112">Administration and Diagnostics</span></span>](../index.md)
