---
title: 如何：使用字元值陣列建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: d9ec897467f0caac0afc089a028516c0316a2bda
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410589"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>如何：使用字元值陣列建立字串 (Visual Basic)
這個範例會從個別字元建立字串 "abcd"。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個方法沒有特殊需求。  
  
 語法 `"a"c` （其中 single `c` 會在單引號後面加上單一字元）是用來建立字元常值。  
  
## <a name="robust-programming"></a>穩固程式設計  
 `Chr(0)`使用字串時，字串中的 Null 字元（相當於）會導致非預期的結果。 Null 字元將會包含在字串中，但在某些情況下，將不會顯示 null 字元之後的字元。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.String>
- [Char 資料類型](../../../language-reference/data-types/char-data-type.md)
- [資料類型](../data-types/index.md)
