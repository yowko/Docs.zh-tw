---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b497231326c640b93b96500df39732104e0f0c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="f4659-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="f4659-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="f4659-103">WS-AT 通訊協定服務已收到「已準備」或「重新執行」訊息，但均來自無法辨識的變動參與者。</span><span class="sxs-lookup"><span data-stu-id="f4659-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="f4659-104">錯誤已傳回給參與者，宣告交易結果不確定。</span><span class="sxs-lookup"><span data-stu-id="f4659-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f4659-105">描述</span><span class="sxs-lookup"><span data-stu-id="f4659-105">Description</span></span>  
 <span data-ttu-id="f4659-106">在本機交易管理員收到來自其已忘記的變動登記之「已準備」或「重新執行」訊息時追蹤。</span><span class="sxs-lookup"><span data-stu-id="f4659-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f4659-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="f4659-107">Troubleshooting</span></span>  
 <span data-ttu-id="f4659-108">調查來自變動參與者的晚期訊息潛在原因。</span><span class="sxs-lookup"><span data-stu-id="f4659-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4659-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4659-109">See Also</span></span>  
 [<span data-ttu-id="f4659-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="f4659-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f4659-111">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="f4659-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f4659-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="f4659-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
