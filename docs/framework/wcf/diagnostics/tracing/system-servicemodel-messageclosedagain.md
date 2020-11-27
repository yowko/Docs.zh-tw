---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: a8aa5e600789df1b64a8a3f1a6355aaae6a6cf4b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294426"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="a6973-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="a6973-102">System.ServiceModel.MessageClosedAgain</span></span>

<span data-ttu-id="a6973-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="a6973-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="a6973-104">描述</span><span class="sxs-lookup"><span data-stu-id="a6973-104">Description</span></span>  

 <span data-ttu-id="a6973-105">已再次關閉訊息。</span><span class="sxs-lookup"><span data-stu-id="a6973-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="a6973-106">訊息應該只關閉一次。</span><span class="sxs-lookup"><span data-stu-id="a6973-106">A message should be closed only once.</span></span> <span data-ttu-id="a6973-107">如果在使用者延伸程式碼中發出這個追蹤，就表示使用者延伸程式碼正在關閉一個已經關閉的訊息。</span><span class="sxs-lookup"><span data-stu-id="a6973-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="a6973-108">如果是透過產品代碼發出這個追蹤，就表示使用者延伸程式碼可能太早關閉訊息。</span><span class="sxs-lookup"><span data-stu-id="a6973-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6973-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6973-109">See also</span></span>

- [<span data-ttu-id="a6973-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="a6973-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="a6973-111">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="a6973-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a6973-112">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="a6973-112">Administration and Diagnostics</span></span>](../index.md)
