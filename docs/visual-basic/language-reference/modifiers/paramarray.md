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
ms.openlocfilehash: be8ddb7f9ba08535d12890d1c5c82a9b7b485f3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597356"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
指定程序參數可選擇性指定的型別元素的陣列。 `ParamArray` 可以是只用於參數清單的最後一個參數。  
  
## <a name="remarks"></a>備註  
 `ParamArray` 可讓您將任意數目的引數傳遞至程序。 A`ParamArray`參數一律宣告使用[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)。  
  
 您可以一或多個引數提供給`ParamArray`藉由傳遞適當的資料陣列的參數類型，以逗號分隔清單的值，或不完全。 如需詳細資訊，請參閱 「 呼叫 ParamArray"[參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)。  
  
> [!IMPORTANT]
>  只要處理陣列，其中可能會無限期地大，會有風險的造成滿溢內部應用程式的容量。 如果您接受參數陣列，從呼叫程式碼，您應該測試它的長度，並採取適當步驟，如果您的應用程式而言太大。  
  
 `ParamArray` 修飾詞可用於以下內容：  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)  
 [參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
