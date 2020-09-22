---
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: baf9303101eea9eed27e8a4eee9e04d255c798e9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867826"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)

指定程式參數接受所指定類型之元素的選擇性陣列。 `ParamArray` 只能用在參數清單的最後一個參數上。  
  
## <a name="remarks"></a>備註  

 `ParamArray` 可讓您將任意數目的引數傳遞至程式。 `ParamArray`一律使用[ByVal](byval.md)宣告參數。  
  
 您可以提供一或多個引數給 `ParamArray` 參數，方法是傳遞適當資料類型的陣列、值的逗點分隔清單，或完全沒有。 如需詳細資料，請參閱 [參數陣列](../../programming-guide/language-features/procedures/parameter-arrays.md)中的「呼叫 ParamArray」。  
  
> [!IMPORTANT]
> 當您處理可能會無限大的陣列時，會有 overrunning 應用程式內部容量的風險。 如果您接受來自呼叫程式碼的參數陣列，您應該測試它的長度，並在對您的應用程式而言太大時採取適當的步驟。  
  
 `ParamArray` 修飾詞可用於以下內容：  
  
 [Declare Statement](../statements/declare-statement.md)  
  
 [Function 陳述式](../statements/function-statement.md)  
  
 [Property Statement](../statements/property-statement.md)  
  
 [Sub 陳述式](../statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [關鍵字](../keywords/index.md)
- [參數陣列](../../programming-guide/language-features/procedures/parameter-arrays.md)
