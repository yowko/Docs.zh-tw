---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: b9dee0fc876c6e7a02d085db7db4bf1c5dd2c68d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816651"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
指定程序參數會採用選擇性的項目指定之型別的陣列。 `ParamArray` 可以用於僅在參數清單的最後一個參數。  
  
## <a name="remarks"></a>備註  
 `ParamArray` 可讓您將任意數目的引數傳遞至程序。 A`ParamArray`參數一律使用宣告[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)。  
  
 您可以一或多個引數提供給`ParamArray`藉由傳遞適當的資料陣列的參數類型，逗號分隔的清單值，或不完全。 如需詳細資訊，請參閱 「 呼叫 ParamArray 」 中[參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)。  
  
> [!IMPORTANT]
>  每當您處理陣列，其中可能會無限期地大，會有風險的造成滿溢內部應用程式的容量。 如果您接受呼叫的程式碼的參數陣列時，您應該測試它的長度，並採取適當步驟，如果它是對您的應用程式而言太大。  
  
 `ParamArray` 修飾詞可用於以下內容：  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
