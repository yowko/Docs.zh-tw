---
title: MustInherit
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 6502da947ae331a26e66d8ce2dbcda46e4172a6e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867961"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)

指定類別只能當做基類使用，而且您無法直接從它建立物件。  
  
## <a name="remarks"></a>備註  

 *基類*的用途 (也稱為*抽象類別*) 是用來定義所有衍生自該類別之類別的通用功能。 這會儲存衍生類別，使其不需要重新定義通用元素。 在某些情況下，這種常見的功能不夠完整，無法建立可用的物件，而且每個衍生類別都會定義遺漏的功能。 在這種情況下，您只想要使用程式碼從衍生類別建立物件。 您會 `MustInherit` 在基類上使用來強制執行此操作。  
  
 類別的另一種用法 `MustInherit` 是將變數限制為一組相關的類別。 您可以定義基類，並從中衍生所有相關的類別。 基類不需要提供所有衍生類別通用的功能，但它可以做為將值指派給變數的篩選準則。 如果您的使用程式碼將變數宣告為基類，Visual Basic 可讓您只將一個衍生類別中的物件指派給該變數。  
  
 .NET Framework 定義數個類別，其中包括、 `MustInherit` <xref:System.Array> <xref:System.Enum> 和 <xref:System.ValueType> 。 <xref:System.ValueType> 是限制變數的基類範例。 所有實數值型別都是衍生自 <xref:System.ValueType> 。 如果您將變數宣告為 <xref:System.ValueType> ，則只能將實數值型別指派給該變數。  
  
## <a name="rules"></a>規則  
  
- **宣告內容。** 您 `MustInherit` 只能在語句中使用 `Class` 。  
  
- **結合的修飾詞。** 您無法 `MustInherit` `NotInheritable` 在相同的宣告中同時指定。  
  
## <a name="example"></a>範例  

 下列範例說明強制繼承和強制覆寫。 基底類別會 `shape` 定義變數 `acrossLine` 。 類別 `circle` 和 `square` 衍生自 `shape` 。 它們會繼承的定義 `acrossLine` ，但必須定義函數， `area` 因為每種形狀的計算都不同。  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 您可以 `shape1` 將和宣告為 `shape2` 類型 `shape` 。 不過，您無法從建立物件， `shape` 因為它缺少函式的功能 `area` 且已標示 `MustInherit` 。  
  
 因為它們是宣告為 `shape` ，所以變數 `shape1` 和 `shape2` 會限制為衍生類別和的物件 `circle` `square` 。 Visual Basic 不允許您將任何其他物件指派給這些變數，以提供高層級的安全性。  
  
## <a name="usage"></a>使用方式  

 `MustInherit`修飾詞可用於此內容中：  
  
 [Class 陳述式](../statements/class-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [Inherits Statement](../statements/inherits-statement.md)
- [NotInheritable](notinheritable.md)
- [關鍵字](../keywords/index.md)
- [繼承基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
