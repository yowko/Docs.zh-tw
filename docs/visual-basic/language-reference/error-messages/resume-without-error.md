---
title: 無錯繼續
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 6dd6805151de52a5e0cf51c520485c0e8558e0a7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870834"
---
# <a name="resume-without-error"></a><span data-ttu-id="a8685-102">無錯繼續</span><span class="sxs-lookup"><span data-stu-id="a8685-102">Resume without error</span></span>

<span data-ttu-id="a8685-103">`Resume`語句出現在錯誤處理常式代碼之外，或即使沒有任何錯誤，程式碼也會跳到錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="a8685-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a8685-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a8685-104">To correct this error</span></span>  
  
1. <span data-ttu-id="a8685-105">請將 `Resume` 語句移至錯誤處理常式，或將其刪除。</span><span class="sxs-lookup"><span data-stu-id="a8685-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="a8685-106">跳至標籤不能跨程式進行，所以請在程式中搜尋識別錯誤處理常式的標籤。</span><span class="sxs-lookup"><span data-stu-id="a8685-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="a8685-107">如果您發現重複的標籤指定為 `GoTo` 不是語句之語句的目標 `On Error GoTo` ，請變更行標籤以同意其預定的目標。</span><span class="sxs-lookup"><span data-stu-id="a8685-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8685-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8685-108">See also</span></span>

- [<span data-ttu-id="a8685-109">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="a8685-109">Resume Statement</span></span>](../statements/resume-statement.md)
- [<span data-ttu-id="a8685-110">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="a8685-110">On Error Statement</span></span>](../statements/on-error-statement.md)
