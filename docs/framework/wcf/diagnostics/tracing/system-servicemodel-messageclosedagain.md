---
title: System.ServiceModel.MessageClosedAgain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f3963fe28ccaf55b3946254e395b770619c8f22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="c28c5-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="c28c5-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="c28c5-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="c28c5-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="c28c5-104">描述</span><span class="sxs-lookup"><span data-stu-id="c28c5-104">Description</span></span>  
 <span data-ttu-id="c28c5-105">已再次關閉訊息。</span><span class="sxs-lookup"><span data-stu-id="c28c5-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="c28c5-106">訊息應該只關閉一次。</span><span class="sxs-lookup"><span data-stu-id="c28c5-106">A message should be closed only once.</span></span> <span data-ttu-id="c28c5-107">如果在使用者延伸程式碼中發出這個追蹤，就表示使用者延伸程式碼正在關閉一個已經關閉的訊息。</span><span class="sxs-lookup"><span data-stu-id="c28c5-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="c28c5-108">如果是透過產品代碼發出這個追蹤，就表示使用者延伸程式碼可能太早關閉訊息。</span><span class="sxs-lookup"><span data-stu-id="c28c5-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c28c5-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c28c5-109">See Also</span></span>  
 [<span data-ttu-id="c28c5-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="c28c5-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c28c5-111">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="c28c5-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="c28c5-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="c28c5-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
