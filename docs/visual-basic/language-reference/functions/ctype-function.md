---
title: CType 函式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 77bff81efbd61a68c054519710bd671d90af1e7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694772"
---
# <a name="ctype-function-visual-basic"></a>CType 函式 (Visual Basic)
傳回運算式明確轉換至指定的資料類型、 物件、 結構、 類別或介面的結果。  
  
## <a name="syntax"></a>語法  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a>組件  
 `expression`  
 任何有效的運算式。 如果值`expression`超出所允許的範圍`typename`，Visual Basic 會擲回的例外狀況。  
  
 `typename`  
 任何運算式中合法`As`子句中的`Dim`陳述式，也就是任何資料類型、 物件、 結構、 類別或介面的名稱。  
  
## <a name="remarks"></a>備註  
  
> [!TIP]
>  您也可以使用下列函式來執行類型轉換：  
>   
>  -   這類類型轉換函式`CByte`， `CDbl`，和`CInt`執行特定的資料型別轉換。 如需詳細資訊，請參閱 <<c0> [ 類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)。  
> -   [DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)或是[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)。 這些運算子需要一種型別繼承自或實作另一個型別。 它們可以提供略微好的效能比`CType`來回轉換時`Object`資料型別。  
  
 `CType` 已編譯的內嵌，這表示，轉換程式碼就會評估運算式的程式碼的一部分。 在某些情況下，更快的程式碼執行因為程序不會呼叫來執行轉換。  
  
 如果沒有任何轉換從定義`expression`要`typename`(例如，從`Integer`至`Date`)，Visual Basic 會顯示編譯時間錯誤訊息。  
  
 如果在執行階段發生轉換失敗，則會擲回適當的例外狀況。 如果縮小轉換失敗，<xref:System.OverflowException>是最常見的結果。 如果轉換，則未定義，<xref:System.InvalidCastException>中擲回。 比方說，如果此情形`expression`屬於型別`Object`不會轉換為其執行階段型別且`typename`。  
  
 資料類型，是否`expression`或是`typename`是類別或結構定義之後，您可以定義`CType`上該類別或結構為轉換運算子。 這可讓`CType`充當*多載運算子*。 如果您這麼做，您可以控制轉換從您的類別或結構，包括可能擲回的例外狀況的行為。  
  
## <a name="overloading"></a>多載化  
 `CType`可以也在類別或結構的程式碼外部定義上多載運算子。 如果您的程式碼將轉換至或從這類類別或結構時，務必了解的行為及其`CType`運算子。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="converting-dynamic-objects"></a>轉換的動態物件  
 動態物件的類型轉換由使用者定義的使用動態轉換<xref:System.Dynamic.DynamicObject.TryConvert%2A>或<xref:System.Dynamic.DynamicMetaObject.BindConvert%2A>方法。 如果您正在使用動態物件，使用<xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A>方法轉換動態物件。  
  
## <a name="example"></a>範例  
 下列範例會使用`CType`函式將轉換運算式，以`Single`資料型別。  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 如需其他範例，請參閱 <<c0> [ 隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換函式](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)
- [如何：定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [.NET Framework 中的型別轉換](../../../standard/base-types/type-conversion.md)
