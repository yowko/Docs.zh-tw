---
title: 宣告的 XML 項目和屬性的名稱 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: dbe85b456f46c40c9cc9a703b38e11992edd24cf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598284"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>宣告的 XML 項目和屬性的名稱 (Visual Basic)
本主題提供 Visual Basic 的指導方針來命名 XML 項目和 XML 常值中的屬性。  在 XML 常值，您可以指定區域名稱或限定的名稱。 限定的名稱是由 XML 命名空間前置詞、 冒號與本機名稱所組成。 如需有關 XML 命名空間前置詞的詳細資訊，請參閱 < [XML 元素常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## <a name="rules"></a>規則  
 項目或屬性在 Visual Basic 中的區域名稱必須遵守下列規則。  
  
- 它可以開始與命名空間。 它必須以字母字元或底線開頭 (`_`)。  
  
- 它必須包含只依字母順序排列的字元、 十進位數字、 底線、 句號 （.）、 和連字號 （-）。  
  
- 它不能超過 1024 個字元。  
  
- 出現在名稱中的冒號表示命名空間的分界。 因此，您可以使用冒號，只是用來指定特定名稱的 XML 命名空間。  
  
 此外，您應遵守下列指導方針。  
  
- XML 1.0 規格會保留所有名稱開頭為"xml"，任何大小寫變化的字串。 因此，請勿使用這些程式元素的名稱和屬性名稱。  
  
### <a name="name-length-guidelines"></a>名稱長度指導方針  
 事實上，名稱應該盡量縮短時仍可清楚識別的項目。 這可改善程式碼的可讀性，並減少列長度和原始程式檔的大小。  
  
 不過，您的名稱不應該簡短，它不會適當地描述項目，或您的程式碼如何使用它。 這是很重要的程式碼的可讀性。 如果其他人嘗試了解它，或您自行查看它很長的時間之後您所撰寫,，適當的項目名稱可以節省時間。  
  
## <a name="case-sensitivity-in-names"></a>在名稱中的區分大小寫  
 XML 項目名稱會區分大小寫。 這表示，當 Visual Basic 編譯器會比較兩個名稱只有字母大小寫不同，它會將它們解譯為不同的名稱。 比方說，它可解譯`ABC`和`abc`做為參考不同的項目。  
  
## <a name="xml-namespaces"></a>XML 命名空間  
 在建立 XML 元素常值時，您可以指定的項目名稱的 XML 命名空間前置詞。 如需詳細資訊，請參閱 < [XML 元素常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
