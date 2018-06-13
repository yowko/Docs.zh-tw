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
ms.openlocfilehash: 5d622c1cff77a45c8de7772af7efbb73586f4400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602836"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
指定類別可用只能當作基底類別，而且您無法直接從它建立物件。  
  
## <a name="remarks"></a>備註  
 目的*基底類別*(也稱為*抽象類別*) 是定義所衍生自它的所有類別通用的功能。 這可以節省衍生的類別不必重新定義通用的項目。 在某些情況下，此常用功能不完整到足以讓可使用的物件，而且每個衍生的類別定義遺漏的功能。 在這種情況下，您會想使用的程式碼，只能從衍生類別中建立物件。 您使用`MustInherit`強制這個基底類別。  
  
 另一個用途`MustInherit`類別是要限制一組相關的類別變數。 您可以定義基底類別，並從它衍生所有相關的類別。 基底類別不需要提供通用於所有的衍生類別中，任何功能，但它可以做為將值指派給變數的篩選。 如果您使用的程式碼會宣告一個變數為基底類別，Visual Basic 可讓您從一個衍生類別的物件只指派給該變數。  
  
 .NET Framework 會定義數個`MustInherit`類別，其間<xref:System.Array>， <xref:System.Enum>，和<xref:System.ValueType>。 <xref:System.ValueType> 是基底類別，以限制變數的範例。 所有實值型別衍生自<xref:System.ValueType>。 如果您將變數宣告為<xref:System.ValueType>，您可以指派只有實值類型給該變數。  
  
## <a name="rules"></a>規則  
  
-   **宣告內容。** 您可以使用`MustInherit`只有`Class`陳述式。  
  
-   **結合的修飾詞。** 您無法指定`MustInherit`搭配`NotInheritable`相同宣告中。  
  
## <a name="example"></a>範例  
 下列範例說明強制的繼承和強制覆寫。 基底類別`shape`定義的變數， `acrossLine`。 類別`circle`和`square`衍生自`shape`。 它們繼承的定義`acrossLine`，但它們必須定義函式`area`因為該計算不同的每一種圖形。  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 您可以宣告`shape1`和`shape2`類型`shape`。 不過，您無法建立從物件`shape`因為其欠缺函式的功能`area`且標示`MustInherit`。  
  
 因為它們會宣告為`shape`，變數`shape1`和`shape2`限於從衍生類別物件`circle`和`square`。 Visual Basic 不允許您將任何其他物件指派給這些變數時，它將提供高層級的型別安全。  
  
## <a name="usage"></a>使用量  
 `MustInherit`修飾詞可用於此內容：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)  
 [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
