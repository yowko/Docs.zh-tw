---
title: 如何：使用字元值陣列建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 08ad2f1c9455853e92533a7f00726c73b6adb87e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071153"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>如何：使用字元值陣列建立字串 (Visual Basic)

此範例會從個別字元建立 "abcd" 字串。  
  
## <a name="example"></a>範例  

 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a>編譯程式碼  

 這個方法沒有特殊需求。  
  
 語法 `"a"c` （單一 `c` 字元後面接著單引號）是用來建立字元常值。  
  
## <a name="robust-programming"></a>穩固程式設計  

 使用字串時，Null 字元 (相當於 `Chr(0)` 字串中的) 會導致非預期的結果。 字串中會包含 null 字元，但在某些情況下，將不會顯示在 null 字元之後的字元。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.String>
- [Char 資料類型](../../../language-reference/data-types/char-data-type.md)
- [Data types (資料類型)](../data-types/index.md)
