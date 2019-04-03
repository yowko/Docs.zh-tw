---
title: 選擇性參數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
ms.openlocfilehash: 4ae2366552426af0107c8d7a35bb5368fe30c8a7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824672"
---
# <a name="optional-parameters-visual-basic"></a>選擇性參數 (Visual Basic)
您可以將程序參數指定為選擇項，當該程序被呼叫時就不必提供引數。 *選擇性參數*由`Optional`程序定義中的關鍵字。 可套用下列規則：  
  
-   程序定義中的每一個選擇性參數都必須指定一個預設值。  
  
-   選擇性參數的預設值必須是常數運算式。  
  
-   在程序定義中，每一個跟在選擇性參數之後的參數也必須是選擇項。  
  
 以下的語法顯示具有選擇性參數的程序宣告：  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a>以選擇性參數呼叫程序  
 當您以選擇性參數呼叫程序時，可以選擇是否提供引數。 如果不提供，則該程序會使用該參數所宣告的預設值。  
  
 當您省略引數清單中的一個或多個選擇性引數時，必須用連續逗號來標示它們的位置。 下列呼叫範例提供第一個和第四個引數，而不提供第二個或第三個引數：  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 下列範例會建立數個對 `MsgBox` 函式的呼叫。 `MsgBox` 會有一個必要參數和兩個選擇性參數。  
  
 第一個對 `MsgBox` 的呼叫會依照 `MsgBox` 定義的引數順序提供這三個引數。 第二個呼叫只會提供必要引數。 第三個和第四個呼叫會提供第一個和第三個引數。 第三個呼叫會依位置執行這個動作，第四個呼叫則會依名稱執行。  
  
 [!code-vb[VbVbcnProcedures#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#47)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a>判斷是否有選擇性引數  
 程序在執行階段時無法偵測指定的引數是否已省略，或者呼叫程式碼已明確提供預設值。 如果您需要有所區別，可以將一個不常用的值設定為預設值。 下列程序定義選擇性參數`office`，並為其預設值的測試`QJZ`，以查看是否在呼叫中將其省略：  
  
 [!code-vb[VbVbcnProcedures#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#46)]  
  
 如果選擇性參數是 `String` 之類的參考類型，您就可以用 `Nothing` 做為預設值，只要不是引數需要的值即可。  
  
## <a name="optional-parameters-and-overloading"></a>選擇性參數和多載化  
 另一個用選擇性參數定義程序的方式是使用多載化 (Overloading)。 如果您有一個選擇性參數，您可以定義程序的兩個多載版本，其中一個接受該參數，而另一個則不接受。 隨著選擇性參數數目的增加，這個方法會變得比較複雜。 但是，它的優點是可以完全確定呼叫程式是否提供每一個選擇性引數。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [參數陣列](./parameter-arrays.md)
- [程序多載化](./procedure-overloading.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
