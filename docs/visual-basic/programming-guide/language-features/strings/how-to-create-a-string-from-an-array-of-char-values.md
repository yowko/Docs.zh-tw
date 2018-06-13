---
title: 如何：使用字元值陣列建立字串 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 104b329011d69e10a2926f31ce5d296759a3cce8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647163"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>如何：使用字元值陣列建立字串 (Visual Basic)
此範例會建立個別字元的字串"abcd"。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個方法沒有任何特殊的需求。  
  
 語法`"a"c`，其中單一`c`在引號內的單一字元後面接著，用來建立字元常值。  
  
## <a name="robust-programming"></a>穩固程式設計  
 Null 字元 (等於`Chr(0)`) 字串中會導致非預期的結果時使用的字串。 Null 字元將會包含在字串中，但在某些情況下不會顯示 null 字元之後。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.String>  
 [Char 資料類型](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
