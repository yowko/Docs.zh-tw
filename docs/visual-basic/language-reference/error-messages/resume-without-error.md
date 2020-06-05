---
title: 無錯繼續
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: b6b565c88acadca048ade22ab00ac68539725f78
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400366"
---
# <a name="resume-without-error"></a><span data-ttu-id="653f4-102">無錯繼續</span><span class="sxs-lookup"><span data-stu-id="653f4-102">Resume without error</span></span>
<span data-ttu-id="653f4-103">`Resume`語句出現在錯誤處理常式代碼之外，或程式碼即使沒有錯誤也會跳入錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="653f4-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="653f4-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="653f4-104">To correct this error</span></span>  
  
1. <span data-ttu-id="653f4-105">請將 `Resume` 語句移至錯誤處理常式，或將它刪除。</span><span class="sxs-lookup"><span data-stu-id="653f4-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="653f4-106">跳到標籤不能在整個程式中發生，因此請搜尋程式中的標籤，找出錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="653f4-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="653f4-107">如果您發現重複的標籤指定為 `GoTo` 不是語句的語句目標 `On Error GoTo` ，請將行標籤變更為同意其預期的目標。</span><span class="sxs-lookup"><span data-stu-id="653f4-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="653f4-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="653f4-108">See also</span></span>

- [<span data-ttu-id="653f4-109">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="653f4-109">Resume Statement</span></span>](../statements/resume-statement.md)
- [<span data-ttu-id="653f4-110">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="653f4-110">On Error Statement</span></span>](../statements/on-error-statement.md)
