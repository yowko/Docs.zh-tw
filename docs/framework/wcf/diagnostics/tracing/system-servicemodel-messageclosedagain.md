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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec4a0acc70f1878756776d7ed8e8d8e5ee64035f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="20b93-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="20b93-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="20b93-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="20b93-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="20b93-104">描述</span><span class="sxs-lookup"><span data-stu-id="20b93-104">Description</span></span>  
 <span data-ttu-id="20b93-105">已再次關閉訊息。</span><span class="sxs-lookup"><span data-stu-id="20b93-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="20b93-106">訊息應該只關閉一次。</span><span class="sxs-lookup"><span data-stu-id="20b93-106">A message should be closed only once.</span></span> <span data-ttu-id="20b93-107">如果在使用者延伸程式碼中發出這個追蹤，就表示使用者延伸程式碼正在關閉一個已經關閉的訊息。</span><span class="sxs-lookup"><span data-stu-id="20b93-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="20b93-108">如果是透過產品代碼發出這個追蹤，就表示使用者延伸程式碼可能太早關閉訊息。</span><span class="sxs-lookup"><span data-stu-id="20b93-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20b93-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20b93-109">See Also</span></span>  
 [<span data-ttu-id="20b93-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="20b93-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="20b93-111">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="20b93-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="20b93-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="20b93-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
