---
title: Friend (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: 756a18da74ff49cbefaf6a63980302bbcb141713
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
指定一或多個宣告的程式設計項目只能從包含其宣告的組件內存取。  
  
## <a name="remarks"></a>備註  
 在許多情況下，您會想程式設計元素，例如類別和結構，以供整個組件，只要其宣告的元件。 不過，您可能不想要讓他們存取組件之外的程式碼 （例如，如果應用程式是專屬的）。 如果您想要限制存取的項目，如此一來，您就可以將它宣告使用`Friend`修飾詞。  
  
 其他的類別、 結構和編譯成相同的模組中的程式碼組件可以存取所有`Friend`該組件中的項目。  
  
 `Friend` 存取通常是慣用的應用程式的程式設計項目層級和`Friend`是介面、 模組、 類別或結構的層級的預設存取權。  
  
 您可以使用`Friend`只在模組、 介面或命名空間層級。 因此，宣告內容`Friend`項目必須是原始程式檔、 命名空間、 介面、 模組、 類別或結構，不能在程序。  
  
 您可以使用`Friend`修飾詞搭配[保護](../../../visual-basic/language-reference/modifiers/protected.md)相同宣告中的修飾詞。 這個組合會授與兩者`Friend`存取，以及上宣告的項目，這樣就可從相同組件，從其自己的類別和衍生類別中的任何位置存取受保護的存取。 您可以指定`Protected Friend`只能在類別成員上。  
  
 如需的比較`Friend`和其他存取修飾詞，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
> [!NOTE]
>  您可以指定另一個組件是 friend 組件，使其可以存取所有類型和成員標記為`Friend`。 如需詳細資訊，請參閱 [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md) (Friend 組件)。  
  
## <a name="example"></a>範例  
 下列類別使用`Friend`修飾詞，以允許存取特定成員相同的組件中的其他程式設計項目。  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a>使用量  
 您可以使用`Friend`修飾詞在這些內容中：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
