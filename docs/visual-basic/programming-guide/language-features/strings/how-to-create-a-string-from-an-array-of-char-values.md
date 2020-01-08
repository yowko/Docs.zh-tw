---
title: 如何：使用字元值陣列建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: bf37ceba901e712df10ad4b39f9ad74194843136
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346776"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>如何：使用字元值陣列建立字串 (Visual Basic)
這個範例會從個別字元建立字串 "abcd"。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個方法沒有特殊需求。  
  
 語法 `"a"c`，其中單一 `c` 遵循引號中的單一字元，用來建立字元常值。  
  
## <a name="robust-programming"></a>最佳化程式設計  
 使用字串時，字串中的 Null 字元（相當於 `Chr(0)`）會導致非預期的結果。 Null 字元將會包含在字串中，但在某些情況下，將不會顯示 null 字元之後的字元。  
  
## <a name="see-also"></a>請參閱

- <xref:System.String>
- [Char 資料類型](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
