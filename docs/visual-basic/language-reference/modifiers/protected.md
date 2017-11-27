---
title: Protected (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0cc7a0cb626a9ec8e2a0e47abc02e5268aed56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)
指定的一或多個宣告的程式設計項目都可以存取只會從他們自己的類別或從衍生類別中。  
  
## <a name="remarks"></a>備註  
 有時類別中宣告的程式設計項目包含機密資料或受限制的程式碼，而且您想要限制存取的項目。 不過，如果是繼承的類別，而您預期的衍生類別階層架構，它可能需要針對這些衍生的類別，以存取資料或程式碼。 在這種情況下，您會想要存取的基底類別和所有衍生類別的項目。 若要限制存取，這種方式中的項目，您可以將它與宣告`Protected`。  
  
## <a name="rules"></a>規則  
  
-   **宣告內容。** 您可以使用`Protected`只能在類別層級。 這表示宣告內容`Protected`項目必須是類別，且不能原始程式檔、 命名空間、 介面、 模組、 結構或程序。  
  
-   **結合的修飾詞。** 您可以使用`Protected`修飾詞搭配[Friend](../../../visual-basic/language-reference/modifiers/friend.md)相同宣告中的修飾詞。 這種組合可讓您可以從相同組件，從其自己的類別和衍生類別的任何位置存取宣告的項目。 您可以指定`Protected Friend`只能在類別成員上。  
  
## <a name="behavior"></a>行為  
  
-   **存取層級。** 類別中的所有程式碼可以存取其項目。 任何衍生自基底類別的類別中的程式碼可以存取所有`Protected`基底類別的項目。 這是衍生的所有層代，則為 true。 這表示類別可以存取`Protected`基底類別的基底類別等的項目。  
  
     受保護的存取不是超集或 friend 存取權限的子集。  
  
-   **存取修飾詞。** 指定存取層級的關鍵字稱為*存取修飾詞*。 如需存取修飾詞的比較，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `Protected` 修飾詞可用於以下內容：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
