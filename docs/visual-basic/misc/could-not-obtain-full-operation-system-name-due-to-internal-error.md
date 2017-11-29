---
title: "由於內部錯誤，無法取得完整作業系統名稱"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65796c41d2a9fbd03517e7b15bc6b566ba4364fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="1bfbb-102">由於內部錯誤，無法取得完整作業系統名稱</span><span class="sxs-lookup"><span data-stu-id="1bfbb-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="1bfbb-103">由於內部錯誤，無法取得完整作業系統名稱。</span><span class="sxs-lookup"><span data-stu-id="1bfbb-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="1bfbb-104">這可能是因為目前電腦上沒有 WMI 存在所造成。</span><span class="sxs-lookup"><span data-stu-id="1bfbb-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="1bfbb-105">呼叫 `My.Computer.Info.OSFullName` 屬性失敗。</span><span class="sxs-lookup"><span data-stu-id="1bfbb-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="1bfbb-106">如果目前電腦上未安裝 Windows Management Instrumentation (WMI)，就可能會發生這項失敗。</span><span class="sxs-lookup"><span data-stu-id="1bfbb-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1bfbb-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1bfbb-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="1bfbb-108">將包圍呼叫的 `Try...Catch` 區塊加入 `My.Computer.Info.OSFullName` 屬性中。</span><span class="sxs-lookup"><span data-stu-id="1bfbb-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="1bfbb-109">如需 WMI 及其安裝它的詳細資訊，請移至，並搜尋"Windows Management Instrumentation Core"。</span><span class="sxs-lookup"><span data-stu-id="1bfbb-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bfbb-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bfbb-110">See Also</span></span>  
 [<span data-ttu-id="1bfbb-111">My.Computer.Info.OSFullName 屬性</span><span class="sxs-lookup"><span data-stu-id="1bfbb-111">My.Computer.Info.OSFullName Property</span></span>](http://msdn.microsoft.com/en-us/b3b0fbd1-4dc5-428a-ad04-0d9fc9c2a9be)  
 [<span data-ttu-id="1bfbb-112">例外狀況和 Visual Basic 中的錯誤處理</span><span class="sxs-lookup"><span data-stu-id="1bfbb-112">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="1bfbb-113">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="1bfbb-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
