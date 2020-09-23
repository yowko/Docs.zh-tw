---
title: 如何：存取字串中的字元
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 4ea37c4393a8ece5513327b22c6c0ba4b027c781
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059180"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>如何：在 Visual Basic 中存取字串中的字元

這個範例示範如何使用 <xref:System.String.Chars%2A> 屬性來存取字串中指定位置的字元。  
  
## <a name="example"></a>範例  

 有時候您的字串中的字元和字串內的字元位置會有很大的説明。 您可以將字串視為 (實例) 的字元陣列 `Char` ; 您可以透過屬性參考該字元的索引來抓取特定字元 <xref:System.String.Chars%2A> 。  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 `index`屬性的參數 <xref:System.String.Chars%2A> 是以零為基底。  
  
## <a name="robust-programming"></a>穩固程式設計  

 屬性會傳回 <xref:System.String.Chars%2A> 指定位置的字元。 不過，某些 Unicode 字元可以用一個以上的字元來表示。 如需如何使用 Unicode 字元的詳細資訊，請參閱 [如何：將字串轉換為字元陣列](how-to-convert-a-string-to-an-array-of-characters.md)。  
  
 <xref:System.String.Chars%2A> <xref:System.IndexOutOfRangeException> 如果 `index` 參數大於或等於字串的長度，或小於零，屬性會擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.String.Chars%2A>
- [如何：將字串轉換為字元陣列](how-to-convert-a-string-to-an-array-of-characters.md)
- [在 Visual Basic 中的字串和其他資料類型之間進行轉換](converting-between-strings-and-other-data-types.md)
- [字串](index.md)
