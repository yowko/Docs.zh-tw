---
title: 參數陣列 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: eac637c0fcaaded25a54332b2f1188876ef5f29a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711878"
---
# <a name="parameter-arrays-visual-basic"></a>參數陣列 (Visual Basic)
通常，您無法呼叫多個引數數目比程序宣告指定的程序。 當您需要不定數目的引數時，您可以宣告*參數陣列*，可讓程序以接受參數值的陣列。 您不必知道參數陣列中的項目數，當您定義的程序。 陣列大小取決於個別的程序的每個呼叫。  
  
## <a name="declaring-a-paramarray"></a>宣告參數陣列  
 您使用[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)關鍵字來表示參數清單中的參數陣列。 可套用下列規則：  
  
-   程序可以定義只有一個參數陣列，而且必須是程序定義中的最後一個參數。  
  
-   參數陣列必須傳值方式傳遞。 它是良好的程式設計做法明確納入[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)程序定義中的關鍵字。  
  
-   參數陣列會自動為選擇性的。 其預設值是空的一維陣列，參數陣列的項目型別。  
  
-   之前參數陣列的所有參數必須都是必要的。 參數陣列必須是唯一的選擇性參數。  
  
## <a name="calling-a-paramarray"></a>呼叫的參數陣列  
 當您呼叫定義的參數陣列的程序時，您可以在任何一種以下列方式提供引數：  
  
-   執行任何動作，也就是您可以省略[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)引數。 在此情況下，空的陣列會傳遞至程序。 您也可以傳遞[Nothing](../../../../visual-basic/language-reference/nothing.md)關鍵字，使用相同的效果。  
  
-   任意數目的引數，並以逗號分隔清單。 每個引數的資料類型必須是隱含地轉換成`ParamArray`項目型別。  
  
-   具有相同的項目型別，做為參數陣列的項目類型的陣列。  
  
 在所有情況下，此程序中的程式碼，請將視為具有相同的資料類型之項目的一維陣列的參數陣列`ParamArray`資料型別。  
  
> [!IMPORTANT]
>  每當您處理陣列，其中可能會無限期地大，會有風險的造成滿溢內部應用程式的容量。 如果您接受參數陣列時，您應該測試呼叫程式碼傳遞給它之陣列的大小。 如果您的應用程式太大，請採取適當的步驟。 如需詳細資訊，請參閱 <<c0> [ 陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="example"></a>範例  
 下列範例定義，並呼叫函式`calcSum`。 `ParamArray`參數的修飾詞`args`可讓函式接受可變數目的引數。  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 下列範例定義的程序含有參數陣列，然後傳遞給參數陣列的所有陣列元素的值。  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [選擇性參數](./optional-parameters.md)
- [程序多載化](./procedure-overloading.md)
- [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
