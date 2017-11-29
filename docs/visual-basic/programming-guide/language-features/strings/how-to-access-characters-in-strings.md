---
title: "如何：在 Visual Basic 中存取字串中的字元"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54d604fc08dd97e0e31f9bcec148431374e8ef8f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>如何：在 Visual Basic 中存取字串中的字元
這個範例示範如何使用<xref:System.String.Chars%2A>屬性來存取字串中指定位置處的字元。  
  
## <a name="example"></a>範例  
 有時候很有用，將您的字串與這些字元在字串中的位置中的字元資料。 您可以將視為字串的字元陣列 (`Char`執行個體); 您可以藉由參考到該字元的索引來擷取特定字元<xref:System.String.Chars%2A>屬性。  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 `index`參數<xref:System.String.Chars%2A>屬性是以零為起始。  
  
## <a name="robust-programming"></a>穩固程式設計  
 <xref:System.String.Chars%2A>屬性會傳回指定位置處的字元。 不過，某些 Unicode 字元可以表示由一個以上的字元。 如需有關如何使用 Unicode 字元的詳細資訊，請參閱[How to： 將字串轉換成字元陣列](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)。  
  
 <xref:System.String.Chars%2A>屬性會擲回<xref:System.IndexOutOfRangeException>例外狀況如果`index`參數是大於或等於字串的長度，或如果它小於零  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.String.Chars%2A>  
 [如何：將字串轉換為字元陣列](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [在 Visual Basic 中的字串和其他資料類型之間進行轉換](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [字串](../../../../visual-basic/programming-guide/language-features/strings/index.md)
