---
title: 函式評估已停用，因為先前的函式評估逾時
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 9bdc12e3dc57b440ed9f304201b8ec401db37871
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874074"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>函式評估已停用，因為先前的函式評估逾時

函數評估已停用，因為先前的函數評估超時。若要重新啟用函數評估，請再次執行，或重新開機調試。  
  
 在 Visual Studio 偵錯工具中，運算式會指定程序呼叫，但另一個評估已超時。  
  
 程序呼叫超時的可能原因包括無限迴圈或 *無限迴圈*。 如需詳細資訊，請參閱 [.。。下一個語句](../statements/for-next-statement.md)。  
  
 無限迴圈的特殊案例是 *遞迴*。 如需詳細資訊，請參閱 [遞迴程式](../../programming-guide/language-features/procedures/recursive-procedures.md)。  
  
 **錯誤識別碼：** BC30957  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 可能的話，請判斷先前的函式評估為何，以及造成它的時間。否則，您可能會再次遇到此錯誤。  
  
2. 請再次逐步執行偵錯工具，或終止並重新啟動偵錯工具。  
  
## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](/visualstudio/debugger/debugger-feature-tour)
- [使用偵錯工具巡覽程式碼](/visualstudio/debugger/navigating-through-code-with-the-debugger)
