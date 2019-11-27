---
title: Inherits Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 6e6e9cc9210232059210862f2bda691c57b372d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353232"
---
# <a name="inherits-statement"></a>Inherits Statement
導致目前的類別或介面繼承另一個類別或一組介面的屬性、變數、屬性、程式和事件。  
  
## <a name="syntax"></a>語法  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`basetypenames`|必要。 這個類別衍生來源的類別名稱。<br /><br /> -或-<br /><br /> 這個介面衍生自的介面名稱。 使用逗號來分隔多個名稱。|  
  
## <a name="remarks"></a>備註  
 如果使用，則 `Inherits` 語句必須是類別或介面定義中第一個非空白的非批註行。 它應該緊接在 `Class` 或 `Interface` 語句後面。  
  
 您只能在類別或介面中使用 `Inherits`。 這表示繼承的宣告內容不能是原始程式檔、命名空間、結構、模組、程式或區塊。  
  
## <a name="rules"></a>規則  
  
- **類別繼承。** 如果類別使用 `Inherits` 語句，您只能指定一個基類。  
  
     類別無法繼承自其內嵌套的類別。  
  
- **介面繼承。** 如果介面使用 `Inherits` 語句，您可以指定一或多個基底介面。 您可以從兩個介面繼承，即使它們各自訂具有相同名稱的成員。 如果您這樣做，則執行程式碼必須使用名稱限定性來指定它所要執行的成員。  
  
     介面無法繼承自具有更嚴格存取層級的另一個介面。 例如，`Public` 介面無法繼承自 `Friend` 介面。  
  
     介面無法繼承自其內所嵌套的介面。  
  
 .NET Framework 中的類別繼承範例是 <xref:System.ArgumentException> 類別，它繼承自 <xref:System.SystemException> 類別。 這會提供 <xref:System.ArgumentException> 系統例外狀況所需的所有預先定義屬性和程式，例如 <xref:System.Exception.Message%2A> 屬性和 <xref:System.Exception.ToString%2A> 方法。  
  
 .NET Framework 中的介面繼承範例是 <xref:System.Collections.ICollection> 介面，它會繼承自 <xref:System.Collections.IEnumerable> 介面。 這會導致 <xref:System.Collections.ICollection> 繼承遍歷集合所需的列舉值定義。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Inherits` 語句，顯示名為 `thisClass` 的類別如何繼承名為 `anotherClass`之基類的所有成員。  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>範例  
 下列範例會顯示多個介面的繼承。  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 名為 `thisInterface` 的介面現在包含 <xref:System.IComparable>、<xref:System.IDisposable>和 <xref:System.IFormattable> 介面中的所有定義，而繼承的成員會分別針對兩個物件的類型特定比較提供，釋出已配置的資源，並將物件的值表示為 `String`。 執行 `thisInterface` 的類別必須實作為每一個基底介面的每個成員。  
  
## <a name="see-also"></a>請參閱

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
