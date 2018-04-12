---
title: Implements 子句 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73f66eda29e37fda15b4c838da5a0458684131da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implements-clause-visual-basic"></a>Implements 子句 (Visual Basic)
表示類別或結構的成員提供介面中定義之成員的實作。  
  
## <a name="remarks"></a>備註  
`Implements`關鍵字不相同[Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)。 您使用`Implements`陳述式，以指定的類別或結構實作一或多個介面，您所使用之每個成員然後`Implements`關鍵字來指定哪個介面和成員實作。

如果類別或結構實作介面時，其必須包括`Implements`陳述式之後立即[Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)或[Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)，而且它必須實作所有成員介面定義。

## <a name="reimplementation"></a>重新實作  
在衍生類別中，您可以重新實作介面成員的基底類別實作的。 這是覆寫基底類別成員，在下列方面不同：

- 基底類別成員不需要是[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)必須重新實作。
- 您可以重新實作的成員使用不同的名稱。

`Implements`關鍵字可以使用下列內容：
- [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)
