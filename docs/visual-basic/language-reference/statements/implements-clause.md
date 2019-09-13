---
title: Implements 子句 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: dcd20f21a989c327dcfcf27d5638d500b6e4b6da
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929322"
---
# <a name="implements-clause-visual-basic"></a>Implements 子句 (Visual Basic)
表示類別或結構成員正為介面中定義的成員提供執行。  
  
## <a name="remarks"></a>備註  
關鍵字與[Implements 語句不同。](../../../visual-basic/language-reference/statements/implements-statement.md) `Implements` 您可以使用`Implements`語句來指定類別或結構會執行一或多個介面，然後針對每個成員`Implements`使用關鍵字來指定它所要執行的介面和成員。

如果類別或結構實作為介面，它必須在`Implements` [class 語句](../../../visual-basic/language-reference/statements/class-statement.md)或[structure 語句](../../../visual-basic/language-reference/statements/structure-statement.md)之後加入語句，而且它必須執行介面所定義的所有成員。

## <a name="reimplementation"></a>重新實作  
在衍生類別中，您可以重新執行基類已實作為的介面成員。 這與覆寫基類成員的方式不同，如下所示：

- 基類成員不需要是可覆[寫](../../../visual-basic/language-reference/modifiers/overridable.md)的根據重新實作。
- 您可以使用不同的名稱來重新實現成員。

`Implements`關鍵字可用於下列內容：

- [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)
