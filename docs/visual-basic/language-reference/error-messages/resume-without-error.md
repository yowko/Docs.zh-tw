---
title: 無錯繼續
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 5e45f713a433365b4bbc8286154a3b877b08ec59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597871"
---
# <a name="resume-without-error"></a><span data-ttu-id="e0b39-102">無錯繼續</span><span class="sxs-lookup"><span data-stu-id="e0b39-102">Resume without error</span></span>
<span data-ttu-id="e0b39-103">A`Resume`陳述式出現在錯誤處理程式碼中，外部或程式碼已跳入錯誤處理常式，即使沒有錯誤。</span><span class="sxs-lookup"><span data-stu-id="e0b39-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e0b39-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e0b39-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="e0b39-105">移動`Resume`陳述式 into 錯誤處理常式，或將它刪除。</span><span class="sxs-lookup"><span data-stu-id="e0b39-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2.  <span data-ttu-id="e0b39-106">跳至標籤不會發生跨程序，因此搜尋的程序識別的錯誤處理常式的標籤。</span><span class="sxs-lookup"><span data-stu-id="e0b39-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="e0b39-107">如果您發現重複的標籤，指定為目標的`GoTo`陳述式不`On Error GoTo`陳述式中，變更線條標籤，以符合所要的目標。</span><span class="sxs-lookup"><span data-stu-id="e0b39-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0b39-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0b39-108">See Also</span></span>  
 [<span data-ttu-id="e0b39-109">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="e0b39-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="e0b39-110">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="e0b39-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
