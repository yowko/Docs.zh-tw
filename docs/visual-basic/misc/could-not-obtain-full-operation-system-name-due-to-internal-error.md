---
title: "由於內部錯誤，無法取得完整作業系統名稱"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6e90de5a2fd0699a449e05b9c32e7450b8bdc991
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="531d5-102">由於內部錯誤，無法取得完整作業系統名稱</span><span class="sxs-lookup"><span data-stu-id="531d5-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="531d5-103">由於內部錯誤，無法取得完整作業系統名稱。</span><span class="sxs-lookup"><span data-stu-id="531d5-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="531d5-104">這可能是因為目前電腦上沒有 WMI 存在所造成。</span><span class="sxs-lookup"><span data-stu-id="531d5-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="531d5-105">呼叫 `My.Computer.Info.OSFullName` 屬性失敗。</span><span class="sxs-lookup"><span data-stu-id="531d5-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="531d5-106">如果目前電腦上未安裝 Windows Management Instrumentation (WMI)，就可能會發生這項失敗。</span><span class="sxs-lookup"><span data-stu-id="531d5-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="531d5-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="531d5-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="531d5-108">將包圍呼叫的 `Try...Catch` 區塊加入 `My.Computer.Info.OSFullName` 屬性中。</span><span class="sxs-lookup"><span data-stu-id="531d5-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="531d5-109">如需 WMI 及其安裝它的詳細資訊，請移至，並搜尋"Windows Management Instrumentation Core"。</span><span class="sxs-lookup"><span data-stu-id="531d5-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="531d5-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="531d5-110">See Also</span></span>  
 [<span data-ttu-id="531d5-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="531d5-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [<span data-ttu-id="531d5-112">例外狀況和 Visual Basic 中的錯誤處理</span><span class="sxs-lookup"><span data-stu-id="531d5-112">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="531d5-113">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="531d5-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
