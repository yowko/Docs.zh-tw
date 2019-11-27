---
title: 如何：使用字元值陣列建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 03138a851afc55f735cc66edeb345817428a0452
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344391"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>如何：使用字元值陣列建立字串 (Visual Basic)
這個範例會從個別字元建立字串 "abcd"。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個方法沒有特殊需求。  
  
 語法 `"a"c`，其中單一 `c` 遵循引號中的單一字元，用來建立字元常值。  
  
## <a name="robust-programming"></a>穩固程式設計  
 使用字串時，字串中的 Null 字元（相當於 `Chr(0)`）會導致非預期的結果。 Null 字元將會包含在字串中，但在某些情況下，將不會顯示 null 字元之後的字元。  
  
## <a name="see-also"></a>請參閱

- <xref:System.String>
- [Char 資料類型](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
