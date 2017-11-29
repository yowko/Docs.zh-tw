---
title: "CType 函式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6118ca5f73a0d446842c33859e0623032082bcd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ctype-function-visual-basic"></a>CType 函式 (Visual Basic)
傳回運算式明確轉換指定的資料類型、 物件、 結構、 類別或介面的結果。  
  
## <a name="syntax"></a>語法  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a>組件  
 `expression`  
 任何有效的運算式。 如果值`expression`超出所允許的範圍`typename`，Visual Basic 會擲回的例外狀況。  
  
 `typename`  
 任何運算式中合法`As`中的子句`Dim`陳述式，也就是任何資料類型、 物件、 結構、 類別或介面的名稱。  
  
## <a name="remarks"></a>備註  
  
> [!TIP]
>  您也可以使用下列函數來執行類型轉換：  
>   
>  -   類型轉換函式，例如`CByte`， `CDbl`，和`CInt`來執行特定資料型別轉換。 如需詳細資訊，請參閱[類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)。  
> -   [DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)或[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)。 這些運算子需要一種類型繼承自或實作其他的型別。 它們可以提供稍微較佳的效能比`CType`時的轉換`Object`資料型別。  
  
 `CType`已編譯的內嵌，這表示，轉換程式碼的程式碼可評估運算式的一部分。 在某些情況下，更快的程式碼執行因為程序不會呼叫以執行轉換。  
  
 如果沒有轉換定義從`expression`至`typename`(例如，從`Integer`至`Date`)，Visual Basic 會顯示編譯時間錯誤訊息。  
  
 如果轉換失敗，在執行階段，會擲回適當的例外狀況。 如果有縮小轉換失敗，<xref:System.OverflowException>是最常見的結果。 如果未定義，轉換<xref:System.InvalidCastException>在擲回。 比方說，這種情況`expression`的型別`Object`不轉換成它的執行階段型別且`typename`。  
  
 資料類型，是否`expression`或`typename`是類別或結構，您定義了，您可以定義`CType`上該類別或結構做為轉換運算子。 這可讓`CType`做為*多載運算子*。 如果您這樣做，您可以控制之間的轉換與類別或結構，包括可能會擲回的例外狀況行為。  
  
## <a name="overloading"></a>多載化  
 `CType`運算子也能在類別或您的程式碼之外定義的結構上多載。 如果您的程式碼轉換，或從這類類別或結構，請務必了解的行為及其`CType`運算子。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="converting-dynamic-objects"></a>轉換的動態物件  
 動態物件的類型轉換都是透過使用者定義的動態轉換使用<xref:System.Dynamic.DynamicObject.TryConvert%2A>或<xref:System.Dynamic.DynamicMetaObject.BindConvert%2A>方法。 如果您使用動態物件，使用<xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A>方法，將轉換的動態物件。  
  
## <a name="example"></a>範例  
 下列範例會使用`CType`函式將轉換運算式，以便`Single`資料型別。  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 如需其他範例，請參閱[隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.OverflowException>  
 <xref:System.InvalidCastException>  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換函式](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [如何：定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [.NET Framework 中的型別轉換](http://msdn.microsoft.com/library/ba36154f-064c-47d3-9f05-72f93a7ca96d)
