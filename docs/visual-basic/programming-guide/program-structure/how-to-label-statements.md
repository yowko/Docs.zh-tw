---
title: 作法：Label 陳述式
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 8f04d592c51b6a0630bfe623fd3574555aef9ff8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403209"
---
# <a name="how-to-label-statements-visual-basic"></a>如何：標記陳述式 (Visual Basic)

語句區塊是由以冒號分隔的程式程式碼所組成。 前面加上識別字串或整數的程式程式碼，稱為*標記*。 語句標籤是用來標記程式程式碼，以識別它與語句搭配使用，例如 `On Error Goto` 。

標籤可能是有效的 Visual Basic 識別碼，例如可識別程式設計項目的識別碼，或整數常值。 標籤必須出現在源程式碼首，而且後面必須加上冒號，而不論後面是否緊接著同一行的語句。

編譯器會藉由檢查行的開頭是否符合任何已定義的識別碼來識別標籤。 如果不是，則編譯器會假設它是標籤。

標籤有自己的宣告空間，而且不會干擾其他識別碼。 標籤的範圍是方法的主體。 標籤宣告的優先順序會在任何不明確的情況下。

> [!NOTE]
> 標籤只能用於方法內的可執行語句。

## <a name="to-label-a-line-of-code"></a>為程式程式碼加上標籤

將識別碼（後面接著冒號）放在源程式碼的開頭。

例如，下列幾行程式碼分別標示了 `Jump` 和 `120` ：

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a>另請參閱

- [陳述式](../language-features/statements.md)
- [Declared Element Names](../language-features/declared-elements/declared-element-names.md)
- [程式結構和程式碼慣例](program-structure-and-code-conventions.md)
