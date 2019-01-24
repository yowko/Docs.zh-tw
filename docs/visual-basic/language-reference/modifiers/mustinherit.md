---
title: MustInherit (Visual Basic)
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
ms.openlocfilehash: 7a246e2565ec6d96e828654fef74500c4cf896b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627664"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
指定可用來只當做基底類別的類別，您無法直接從它建立物件。  
  
## <a name="remarks"></a>備註  
 目的*基底類別*(也稱為*抽象類別*) 是定義從它衍生的所有類別的通用功能。 這讓衍生的類別不必重新定義的通用元素。 在某些情況下，此常用功能不夠完整，若要使用的物件，並不會定義每個衍生的類別缺少的功能。 在此情況下，您只能從衍生類別中建立物件使用的程式碼。 您使用`MustInherit`在強制執行此基底類別。  
  
 另一個使用`MustInherit`類別是限制一組相關的類別變數。 您可以定義基底類別，並從中衍生所有這些相關的類別。 基底類別不需要提供任何功能通用於所有衍生的類別，但它可以做為篩選，以將值指派給變數。 如果您使用的程式碼會宣告一個變數的基底類別，Visual Basic 可讓您指派給只從其中一個衍生的類別，該變數。  
  
 .NET Framework 會定義數個`MustInherit`類別，在它們之間<xref:System.Array>， <xref:System.Enum>，和<xref:System.ValueType>。 <xref:System.ValueType> 是基底類別，可限制變數的範例。 所有實值型別衍生自<xref:System.ValueType>。 如果您宣告變數，以做為<xref:System.ValueType>，您可以將實值型別只能指派給該變數。  
  
## <a name="rules"></a>規則  
  
-   **宣告內容。** 您可以使用`MustInherit`只能在`Class`陳述式。  
  
-   **結合的修飾詞。** 您無法指定`MustInherit`搭配`NotInheritable`相同宣告中。  
  
## <a name="example"></a>範例  
 下列範例說明強制的繼承和強制覆寫。 基底類別`shape`定義的變數， `acrossLine`。 類別`circle`並`square`衍生自`shape`。 它們繼承的定義`acrossLine`，但它們必須定義函式`area`由於該計算各有不同的每一種圖形。  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 您可以宣告`shape1`並`shape2`是類型`shape`。 不過，您無法建立物件的`shape`因為其欠缺函式的功能`area`，並標示`MustInherit`。  
  
 因為它們會宣告為`shape`，變數`shape1`並`shape2`限於從衍生類別物件`circle`和`square`。 Visual Basic 不允許您將任何其他物件指派給這些變數時，它將提供高層級的型別安全。  
  
## <a name="usage"></a>使用量  
 `MustInherit`修飾詞，請使用此內容中：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>另請參閱
- [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
