---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: ab1c2c8afe3a66536810a614cc6deac12519cb9b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599629"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="020ed-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="020ed-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="020ed-103">WS-AT 通訊協定服務已收到「已準備」或「重新執行」訊息，但均來自無法辨識的變動參與者。</span><span class="sxs-lookup"><span data-stu-id="020ed-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="020ed-104">錯誤已傳回給參與者，宣告異動結果不確定。</span><span class="sxs-lookup"><span data-stu-id="020ed-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="020ed-105">描述</span><span class="sxs-lookup"><span data-stu-id="020ed-105">Description</span></span>  
 <span data-ttu-id="020ed-106">在本機異動管理員收到來自其已忘記的變動登記之「已準備」或「重新執行」訊息時追蹤。</span><span class="sxs-lookup"><span data-stu-id="020ed-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="020ed-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="020ed-107">Troubleshooting</span></span>  
 <span data-ttu-id="020ed-108">調查來自變動參與者的晚期訊息潛在原因。</span><span class="sxs-lookup"><span data-stu-id="020ed-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="020ed-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="020ed-109">See also</span></span>

- [<span data-ttu-id="020ed-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="020ed-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="020ed-111">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="020ed-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="020ed-112">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="020ed-112">Administration and Diagnostics</span></span>](../index.md)
