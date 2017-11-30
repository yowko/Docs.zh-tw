---
title: "如何：使用字元值陣列建立字串 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06e5c6923c26f3cb84b38475d6680523853d727d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
