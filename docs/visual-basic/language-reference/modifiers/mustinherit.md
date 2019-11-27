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
ms.openlocfilehash: 30befaaf194d78d26a57f29c59bf0a603e9f07a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351502"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
指定類別只能當做基類使用，而且您無法直接從它建立物件。  
  
## <a name="remarks"></a>備註  
 *基類*（也稱為*抽象類別*）的目的，是要定義所有衍生自它的類別通用的功能。 如此一來，衍生的類別就必須重新定義通用元素。 在某些情況下，這個常見的功能並不足以建立可用的物件，而每個衍生的類別會定義遺漏的功能。 在這種情況下，您會想要使用的程式碼只從衍生類別建立物件。 您會在基類上使用 `MustInherit` 來強制執行此操作。  
  
 `MustInherit` 類別的另一個用法是將變數限制為一組相關的類別。 您可以定義基類，並從該類別衍生所有相關的類別。 基類不需要提供所有衍生類別通用的任何功能，但它可以做為將值指派給變數的篩選準則。 如果您的取用程式碼將變數宣告為基類，Visual Basic 可讓您只將一個衍生類別中的物件指派給該變數。  
  
 .NET Framework 會定義數個 `MustInherit` 類別，其中 <xref:System.Array>、<xref:System.Enum>和 <xref:System.ValueType>。 <xref:System.ValueType> 是限制變數之基類的範例。 所有實值型別都是衍生自 <xref:System.ValueType>。 如果您將變數宣告為 <xref:System.ValueType>，就只能將實數值型別指派給該變數。  
  
## <a name="rules"></a>規則  
  
- **宣告內容。** 您只能在 `Class` 語句中使用 `MustInherit`。  
  
- **合併的修飾詞。** 您不能在相同的宣告中同時指定與 `NotInheritable` `MustInherit`。  
  
## <a name="example"></a>範例  
 下列範例說明強制繼承和強制覆寫。 基底類別 `shape` 定義變數 `acrossLine`。 `circle` 和 `square` 衍生自 `shape`的類別。 它們會繼承 `acrossLine`的定義，但是必須定義函式 `area`，因為每一種形狀的計算都不同。  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 您可以宣告 `shape1`，並 `shape2` `shape`的類型。 不過，您無法從 `shape` 建立物件，因為它缺少函式 `area` 的功能，而且已標記為 `MustInherit`。  
  
 因為它們宣告為 `shape`，`shape1` 和 `shape2` 的變數會限制為衍生類別 `circle` 和 `square`中的物件。 Visual Basic 不允許您將任何其他物件指派給這些變數，這會提供高階的型別安全。  
  
## <a name="usage"></a>使用方式  
 `MustInherit` 修飾詞可以在此內容中使用：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>請參閱

- [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
