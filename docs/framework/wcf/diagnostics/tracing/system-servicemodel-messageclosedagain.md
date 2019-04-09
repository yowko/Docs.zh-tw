---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: a18355d55359df665d0e936ce95da34bf07aec6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181326"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="d067c-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="d067c-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="d067c-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="d067c-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="d067c-104">描述</span><span class="sxs-lookup"><span data-stu-id="d067c-104">Description</span></span>  
 <span data-ttu-id="d067c-105">已再次關閉訊息。</span><span class="sxs-lookup"><span data-stu-id="d067c-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="d067c-106">訊息應該只關閉一次。</span><span class="sxs-lookup"><span data-stu-id="d067c-106">A message should be closed only once.</span></span> <span data-ttu-id="d067c-107">如果在使用者延伸程式碼中發出這個追蹤，就表示使用者延伸程式碼正在關閉一個已經關閉的訊息。</span><span class="sxs-lookup"><span data-stu-id="d067c-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="d067c-108">如果是透過產品代碼發出這個追蹤，就表示使用者延伸程式碼可能太早關閉訊息。</span><span class="sxs-lookup"><span data-stu-id="d067c-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d067c-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d067c-109">See also</span></span>

- [<span data-ttu-id="d067c-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="d067c-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="d067c-111">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="d067c-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d067c-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="d067c-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
