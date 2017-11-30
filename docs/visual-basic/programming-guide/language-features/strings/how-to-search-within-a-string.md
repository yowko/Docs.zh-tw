---
title: "如何：在字串內搜尋 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c828d0b32fdf90e121e9d5da0bb60ab11c212f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
