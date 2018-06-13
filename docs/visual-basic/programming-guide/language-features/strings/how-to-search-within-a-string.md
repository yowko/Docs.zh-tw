---
title: 如何：在字串內搜尋 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 08a005f2927a76c9b29c1ff0092ea8282188b2b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647679"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>如何：在字串內搜尋 (Visual Basic)
這個範例會呼叫<xref:System.String.IndexOf%2A>方法<xref:System.String>来報告的第一個子字串索引的物件。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   `Imports`陳述式指定<xref:System>命名空間。 如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## <a name="robust-programming"></a>穩固程式設計  
 <xref:System.String.IndexOf%2A>方法會回報第一個子字串的第一個字元的位置。 索引是以 0 為基礎，這表示字串的第一個字元索引為 0。  
  
 如果<xref:System.String.IndexOf%2A>找不到子字串，則傳回-1。  
  
 <xref:System.String.IndexOf%2A>方法會區分大小寫，而且會使用目前文化特性。  
  
 您可能要括住的字串搜尋，在最佳錯誤控制項`Try`區塊[再試一次...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)建構。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.String.IndexOf%2A>  
 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [字串](../../../../visual-basic/programming-guide/language-features/strings/index.md)
