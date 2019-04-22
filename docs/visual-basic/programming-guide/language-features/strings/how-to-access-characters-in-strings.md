---
title: HOW TO：在 Visual Basic 中的字串中的存取字元
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 840a769b0bb322ef7b878a312437c5ec200ab074
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834487"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>HOW TO：在 Visual Basic 中的字串中的存取字元
此範例示範如何使用<xref:System.String.Chars%2A>屬性來存取字串中指定的位置處的字元。  
  
## <a name="example"></a>範例  
 有時候最好擁有您的字串與這些字元在字串中的位置中的字元資料。 您可以將字串視為字元陣列 (`Char`執行個體)，您可以藉由參考到該字元的索引來擷取特定字元<xref:System.String.Chars%2A>屬性。  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 `index`參數<xref:System.String.Chars%2A>屬性是以零為起始。  
  
## <a name="robust-programming"></a>穩固程式設計  
 <xref:System.String.Chars%2A>屬性會傳回指定位置處的字元。 不過，某些 Unicode 字元可以表示多個字元。 如需有關如何使用 Unicode 字元的詳細資訊，請參閱[How to:將字串轉換為字元陣列](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)。  
  
 <xref:System.String.Chars%2A>屬性會擲回<xref:System.IndexOutOfRangeException>例外狀況如果`index`參數是否大於或等於字串的長度，或如果它小於零  
  
## <a name="see-also"></a>另請參閱

- <xref:System.String.Chars%2A>
- [如何：將字串轉換為字元陣列](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [在 Visual Basic 中的字串和其他資料類型之間進行轉換](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [字串](../../../../visual-basic/programming-guide/language-features/strings/index.md)
