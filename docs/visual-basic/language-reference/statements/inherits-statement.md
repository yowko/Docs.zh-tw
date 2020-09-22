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
ms.openlocfilehash: dd8fbc71fdc859bb127764951464278267c0984c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875232"
---
# <a name="inherits-statement"></a>Inherits Statement

導致目前的類別或介面繼承其他類別或介面集的屬性、變數、屬性、程式和事件。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`basetypenames`|必要。 這個類別所衍生的類別名稱。<br /><br /> -或-<br /><br /> 這個介面衍生自的介面名稱。 使用逗號來分隔多個名稱。|  
  
## <a name="remarks"></a>備註  

 如果使用的話， `Inherits` 語句必須是類別或介面定義中的第一個非空白的非批註行。 它應該緊接在 `Class` 或 `Interface` 語句後面。  
  
 您 `Inherits` 只能在類別或介面中使用。 這表示繼承的宣告內容不能是原始程式檔、命名空間、結構、模組、程式或區塊。  
  
## <a name="rules"></a>規則  
  
- **類別繼承。** 如果類別使用 `Inherits` 語句，您只能指定一個基類。  
  
     類別無法繼承自其內嵌套的類別。  
  
- **介面繼承。** 如果介面使用 `Inherits` 語句，您可以指定一或多個基底介面。 您可以繼承自兩個介面，即使它們各自訂了相同名稱的成員。 如果您這樣做，執行程式碼必須使用名稱限定性來指定所要執行的成員。  
  
     介面無法繼承自另一個具有較嚴格存取層級的介面。 例如， `Public` 介面無法從 `Friend` 介面繼承。  
  
     介面無法繼承自其內嵌套的介面。  
  
 .NET Framework 中類別繼承的範例是 <xref:System.ArgumentException> 繼承自類別的類別 <xref:System.SystemException> 。 這會提供 <xref:System.ArgumentException> 系統例外狀況所需的所有預先定義屬性和程式，例如 <xref:System.Exception.Message%2A> 屬性和 <xref:System.Exception.ToString%2A> 方法。  
  
 .NET Framework 中的介面繼承範例是 <xref:System.Collections.ICollection> 繼承自介面的介面 <xref:System.Collections.IEnumerable> 。 這會使 <xref:System.Collections.ICollection> 繼承集合所需的列舉值的定義。  
  
## <a name="example"></a>範例  

 下列範例 `Inherits` 會使用語句來顯示名為的類別如何 `thisClass` 繼承名為之基類的所有成員 `anotherClass` 。  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>範例  

 下列範例顯示多個介面的繼承。  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 名為的介面 `thisInterface` 現在包含、和介面中的所有定義， <xref:System.IComparable> <xref:System.IDisposable> 而 <xref:System.IFormattable> 繼承的成員會分別針對兩個物件的類型特定比較提供，釋出配置的資源，並將物件的值表示為 `String` 。 實作為的類別 `thisInterface` 必須執行每個基底介面的每個成員。  
  
## <a name="see-also"></a>另請參閱

- [MustInherit](../modifiers/mustinherit.md)
- [NotInheritable](../modifiers/notinheritable.md)
- [物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)
- [繼承基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [介面](../../programming-guide/language-features/interfaces/index.md)
