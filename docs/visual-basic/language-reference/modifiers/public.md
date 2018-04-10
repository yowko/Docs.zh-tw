---
title: Public (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6cd70adf6ec31c56f39d0443d320dd1b00b00d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
指定一或多個宣告的程式設計項目有沒有存取限制。  
  
## <a name="remarks"></a>備註  
 如果您要發佈的元件或一組元件，例如類別程式庫，您通常會想要與您的組件相互操作的任何程式碼可存取的程式設計項目。 若要授與這類項目上的無限制的存取，您可以宣告它與`Public`。  
  
 公用存取您不需要限制存取時的一般程式設計項目層級。 請注意，元素的存取層級宣告介面、 模組、 類別或結構中的預設值為`Public`如果您不要否則宣告它。  
  
## <a name="rules"></a>規則  
  
-   **宣告內容。** 您可以使用`Public`只能在模組、 介面或命名空間層級。 這表示宣告內容`Public`項目必須是原始程式檔、 命名空間、 介面、 模組、 類別或結構，且不能在程序。  
  
## <a name="behavior"></a>行為  
  
-   **存取層級。** 模組、 類別或結構可以存取的所有程式碼可以存取其`Public`項目。  
  
-   **預設存取權。** 內部程序預設值為公用存取，因此您的本機變數無法在其上使用任何存取修飾詞。  
  
-   **存取修飾詞。** 指定存取層級的關鍵字稱為*存取修飾詞*。 如需存取修飾詞的比較，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `Public` 修飾詞可用於以下內容：  
  
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
  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
