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
ms.openlocfilehash: 5d88a01f90bc91a88229d19aa2368f8c71075b2f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404495"
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
 如果使用，則 `Inherits` 語句必須是類別或介面定義中第一個非空白的非批註行。 它應該緊接在 `Class` 或 `Interface` 語句之後。  
  
 您 `Inherits` 只能在類別或介面中使用。 這表示繼承的宣告內容不能是原始程式檔、命名空間、結構、模組、程式或區塊。  
  
## <a name="rules"></a>規則  
  
- **類別繼承。** 如果類別使用 `Inherits` 語句，您只能指定一個基類。  
  
     類別無法繼承自其內嵌套的類別。  
  
- **介面繼承。** 如果介面使用 `Inherits` 語句，您可以指定一或多個基底介面。 您可以從兩個介面繼承，即使它們各自訂具有相同名稱的成員。 如果您這樣做，則執行程式碼必須使用名稱限定性來指定它所要執行的成員。  
  
     介面無法繼承自具有更嚴格存取層級的另一個介面。 例如， `Public` 介面無法繼承自 `Friend` 介面。  
  
     介面無法繼承自其內所嵌套的介面。  
  
 .NET Framework 中類別繼承的範例 <xref:System.ArgumentException> ，是繼承自類別的類別 <xref:System.SystemException> 。 這會提供給 <xref:System.ArgumentException> 系統例外狀況所需的所有預先定義屬性和程式，例如 <xref:System.Exception.Message%2A> 屬性和 <xref:System.Exception.ToString%2A> 方法。  
  
 .NET Framework 中的介面繼承範例是 <xref:System.Collections.ICollection> 介面，它會繼承自 <xref:System.Collections.IEnumerable> 介面。 這會導致 <xref:System.Collections.ICollection> 繼承集合所需的列舉值定義。  
  
## <a name="example"></a>範例  
 下列範例 `Inherits` 會使用語句來顯示名稱為的類別如何 `thisClass` 繼承名為之基類的所有成員 `anotherClass` 。  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>範例  
 下列範例會顯示多個介面的繼承。  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 名為的介面 `thisInterface` 現在包含、和介面中的所有定義，而 <xref:System.IComparable> 繼承的成員會 <xref:System.IDisposable> <xref:System.IFormattable> 分別提供兩個物件的類型特定比較、釋放已配置的資源，以及將物件的值表示為 `String` 。 執行的類別 `thisInterface` 必須實作為每一個基底介面的每個成員。  
  
## <a name="see-also"></a>另請參閱

- [MustInherit](../modifiers/mustinherit.md)
- [NotInheritable](../modifiers/notinheritable.md)
- [物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)
- [繼承基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [介面](../../programming-guide/language-features/interfaces/index.md)
