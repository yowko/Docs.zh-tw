---
title: HOW TO：從 Char 值 (Visual Basic) 的陣列建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 0d3a4caf0967ab77de7d91470e43e52521dbd2da
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975507"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>HOW TO：從 Char 值 (Visual Basic) 的陣列建立字串
此範例會建立從個別字元的字串"abcd"。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個方法沒有任何特殊的需求。  
  
 語法`"a"c`，其中單一`c`會遵循在引號內的單一字元，用來建立字元常值。  
  
## <a name="robust-programming"></a>穩固程式設計  
 Null 字元 (等於`Chr(0)`) 字串中會導致非預期的結果時使用的字串。 Null 字元會包含字串，但在某些情況下不會顯示在 null 字元後面的字元。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.String>
- [Char 資料類型](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
