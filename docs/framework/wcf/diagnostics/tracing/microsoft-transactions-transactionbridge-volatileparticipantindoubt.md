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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 98ce61e4a46f8853e61e0ef44fdc78cf3e94431a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="33e36-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="33e36-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="33e36-103">WS-AT 通訊協定服務已收到「已準備」或「重新執行」訊息，但均來自無法辨識的變動參與者。</span><span class="sxs-lookup"><span data-stu-id="33e36-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="33e36-104">錯誤已傳回給參與者，宣告交易結果不確定。</span><span class="sxs-lookup"><span data-stu-id="33e36-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="33e36-105">描述</span><span class="sxs-lookup"><span data-stu-id="33e36-105">Description</span></span>  
 <span data-ttu-id="33e36-106">在本機交易管理員收到來自其已忘記的變動登記之「已準備」或「重新執行」訊息時追蹤。</span><span class="sxs-lookup"><span data-stu-id="33e36-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="33e36-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="33e36-107">Troubleshooting</span></span>  
 <span data-ttu-id="33e36-108">調查來自變動參與者的晚期訊息潛在原因。</span><span class="sxs-lookup"><span data-stu-id="33e36-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e36-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33e36-109">See Also</span></span>  
 [<span data-ttu-id="33e36-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="33e36-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="33e36-111">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="33e36-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="33e36-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="33e36-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
