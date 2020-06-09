---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: d341953b8e12b14e6a3fe8a477c16a1b3a4454ae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84580433"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="21a0d-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="21a0d-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="21a0d-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="21a0d-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="21a0d-104">描述</span><span class="sxs-lookup"><span data-stu-id="21a0d-104">Description</span></span>  
 <span data-ttu-id="21a0d-105">已再次關閉訊息。</span><span class="sxs-lookup"><span data-stu-id="21a0d-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="21a0d-106">訊息應該只關閉一次。</span><span class="sxs-lookup"><span data-stu-id="21a0d-106">A message should be closed only once.</span></span> <span data-ttu-id="21a0d-107">如果在使用者延伸程式碼中發出這個追蹤，就表示使用者延伸程式碼正在關閉一個已經關閉的訊息。</span><span class="sxs-lookup"><span data-stu-id="21a0d-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="21a0d-108">如果是透過產品代碼發出這個追蹤，就表示使用者延伸程式碼可能太早關閉訊息。</span><span class="sxs-lookup"><span data-stu-id="21a0d-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a0d-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="21a0d-109">See also</span></span>

- [<span data-ttu-id="21a0d-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="21a0d-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="21a0d-111">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="21a0d-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="21a0d-112">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="21a0d-112">Administration and Diagnostics</span></span>](../index.md)
