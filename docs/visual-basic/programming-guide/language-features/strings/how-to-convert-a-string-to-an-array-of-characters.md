---
title: "如何：在 Visual Basic 中將字串轉換為字元陣列"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59d0da52c8f78b93c76325e6242156c106deeaf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>如何：在 Visual Basic 中將字串轉換為字元陣列
有時候很有用的字元，在您的字串與您在字串內，例如當您在剖析字串的字元位置的資料。 此範例示範如何取得陣列的字元字串中藉由呼叫的字串<xref:System.String.ToCharArray%2A>方法。  
  
## <a name="example"></a>範例  
 這個範例示範如何分割字串成`Char`陣列，以及如何分割字串成`String`Unicode 文字字元的陣列。 此差異的原因是 Unicode 文字字元所組成兩個或多個`Char`字元 (例如 surrogate 字組或結合字元序列)。 如需詳細資訊，請參閱<xref:System.Globalization.TextElementEnumerator>和 「 Unicode 標準 「 http://www.unicode.org。  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>範例  
 更難以將字串分隔為 Unicode 文字字元，但這是需要字串的視覺表示方式的相關資訊。 這個範例會使用<xref:System.Globalization.StringInfo.SubstringByTextElements%2A>方法來取得 Unicode 文字字元字串所組成的相關資訊。  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [如何：存取字串中的字元](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [在 Visual Basic 中的字串和其他資料類型之間進行轉換](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [字串](../../../../visual-basic/programming-guide/language-features/strings/index.md)
