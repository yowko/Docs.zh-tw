---
title: Overridable (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f7d5dd33f8591be1b4305e954e55e035882626c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)
指定的屬性或程序可覆寫的同名的屬性或衍生類別中的程序。  
  
## <a name="remarks"></a>備註  
 `Overridable`修飾詞允許在衍生類別中覆寫類別中的屬性或方法。 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)修飾詞可防止屬性或方法在衍生類別中覆寫。  如需詳細資訊，請參閱[繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。  
  
 如果`Overridable`或`NotOverridable`修飾詞未指定，預設值取決於是否屬性或方法會覆寫基底類別屬性或方法。 如果屬性或方法覆寫基底類別屬性或方法，預設值是`Overridable`; 否則它是`NotOverridable`。  
  
 您可以遮蔽或覆寫，以重新定義繼承的項目，但有兩種方法之間的重大差異。 如需詳細資訊，請參閱[Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
 會覆寫的項目有時稱為*虛擬*項目。 如果它會覆寫，但不是一定要有時也稱為*具體*項目。  
  
 您只能在屬性或程序宣告陳述式中使用 `Overridable`。  
  
## <a name="combined-modifiers"></a>結合的修飾詞  
 您無法指定`Overridable`或`NotOverridable`如`Private`方法。  
  
 您無法指定`Overridable`搭配`MustOverride`， `NotOverridable`，或`Shared`相同宣告中。  
  
 因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。  
  
## <a name="usage"></a>使用方式  
 `Overridable` 修飾詞可用於以下內容：  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [修飾詞](../../../visual-basic/language-reference/modifiers/index.md)  
 [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
