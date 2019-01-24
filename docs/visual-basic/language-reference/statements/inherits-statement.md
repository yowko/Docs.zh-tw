---
title: Inherits 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 329b4f68874d29d141001800ed326a454a878ab8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502894"
---
# <a name="inherits-statement"></a>Inherits Statement
會導致目前的類別或介面從另一個類別或介面集合繼承屬性、 變數、 屬性、 程序和事件。  
  
## <a name="syntax"></a>語法  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`basetypenames`|必要項。 從這個類別衍生的類別名稱。<br /><br /> -或-<br /><br /> 從這個介面衍生的介面名稱。 使用逗號來分隔多個名稱。|  
  
## <a name="remarks"></a>備註  
 如果使用，`Inherits`陳述式必須是類別或介面定義中的第一個非空白的非註解一行。 它應該緊接`Class`或`Interface`陳述式。  
  
 您可以使用`Inherits`只能在類別或介面中。 這表示原始程式檔、 命名空間、 結構、 模組、 程序或區塊，不能繼承的宣告內容。  
  
## <a name="rules"></a>規則  
  
-   **類別繼承。** 如果類別會使用`Inherits`陳述式中，您可以指定只有一個基底類別。  
  
     類別無法繼承自巢狀類別。  
  
-   **介面繼承。** 如果介面使用`Inherits`陳述式中，您可以指定一或多個基底介面。 您可以繼承自兩個介面，即使它們都各自定義具有相同名稱的成員。 如果您這樣做時，實作程式碼必須使用名稱限定性條件來指定它所實作的成員。  
  
     介面無法繼承自另一個介面具有更嚴格的存取層級。 例如，`Public`介面無法繼承自`Friend`介面。  
  
     介面無法繼承自的巢狀介面。  
  
 舉例來說，.NET Framework 中的類別繼承<xref:System.ArgumentException>類別，繼承自<xref:System.SystemException>類別。 這提供<xref:System.ArgumentException>所有預先定義的屬性和程序所需的系統例外狀況，例如<xref:System.Exception.Message%2A>屬性和<xref:System.Exception.ToString%2A>方法。  
  
 舉例來說，.NET Framework 中的介面繼承<xref:System.Collections.ICollection>介面，繼承自<xref:System.Collections.IEnumerable>介面。 這會導致<xref:System.Collections.ICollection>繼承需要周遊集合的列舉值的定義。  
  
## <a name="example"></a>範例  
 下列範例會使用`Inherits`陳述式來顯示類別的命名方式`thisClass`可以繼承的基底類別，名為的所有成員`anotherClass`。  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例顯示多個介面的繼承。  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 名為介面`thisInterface`現在包含中的所有定義<xref:System.IComparable>， <xref:System.IDisposable>，和<xref:System.IFormattable>介面繼承的成員分別提供針對特定類型的比較的兩個物件，釋放配置的資源表示為物件的值和`String`。 類別若實作`thisInterface`必須實作每個基底介面的每個成員。  
  
## <a name="see-also"></a>另請參閱
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
