---
title: 如何：存取字串中的字元
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: fa5920cfd25f61f6e6c7d5438ef7c0e38a48fa1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401949"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>如何：在 Visual Basic 中存取字串中的字元
這個範例示範如何使用 <xref:System.String.Chars%2A> 屬性來存取字串中指定位置的字元。  
  
## <a name="example"></a>範例  
 如果您的字串中有字元的資料，以及字串內這些字元的位置，有時會很有説明。 您可以將字串視為字元陣列（ `Char` 實例）; 您可以透過屬性參考該字元的索引來抓取特定字元 <xref:System.String.Chars%2A> 。  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 `index`屬性的參數 <xref:System.String.Chars%2A> 是以零為基底。  
  
## <a name="robust-programming"></a>穩固程式設計  
 屬性會傳回 <xref:System.String.Chars%2A> 指定位置的字元。 不過，某些 Unicode 字元可以用一個以上的字元來表示。 如需如何使用 Unicode 字元的詳細資訊，請參閱[如何：將字串轉換為字元陣列](how-to-convert-a-string-to-an-array-of-characters.md)。  
  
 <xref:System.String.Chars%2A> <xref:System.IndexOutOfRangeException> 如果 `index` 參數大於或等於字串的長度，或如果小於零，則屬性會擲回例外狀況  
  
## <a name="see-also"></a>另請參閱

- <xref:System.String.Chars%2A>
- [如何：將字串轉換為字元陣列](how-to-convert-a-string-to-an-array-of-characters.md)
- [在 Visual Basic 中的字串和其他資料類型之間進行轉換](converting-between-strings-and-other-data-types.md)
- [字串](index.md)
