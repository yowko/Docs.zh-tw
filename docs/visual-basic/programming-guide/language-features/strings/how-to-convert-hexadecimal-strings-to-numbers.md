---
title: "如何：將十六進位字串轉換為數字 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6b1beae273fa737ca7c95a253d95c947e760f9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>如何：將十六進位字串轉換為數字 (Visual Basic)
這個範例會將十六進位字串轉換成整數使用<xref:System.Convert.ToInt32%2A>方法。  
  
### <a name="to-convert-a-hexadecimal-string-to-a-number"></a>若要將十六進位字串轉換為數字  
  
-   使用<xref:System.Convert.ToInt32%2A>方法，將轉換的數字表示為整數的基底為 16。  
  
     第一個引數<xref:System.Convert.ToInt32%2A>方法是要轉換的字串。 第二個引數描述哪些; 表示的數字的基底十六進位為基底 16。  
  
     [!code-vb[VbVbalrStrings#62](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A>
