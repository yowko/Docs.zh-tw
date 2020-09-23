---
title: 宣告的 XML 元素和屬性名稱
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 2142674c3de4c5ac9e806c1328daa3efb697beb9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085616"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>宣告的 XML 項目和屬性的名稱 (Visual Basic)

本主題提供在 XML 常值中命名 XML 元素和屬性的 Visual Basic 指導方針。  在 XML 常值中，您可以指定本機名稱或限定名稱。 限定名稱是由 XML 命名空間前置詞、冒號和區功能變數名稱稱所組成。 如需 XML 命名空間前置詞的詳細資訊，請參閱 [Xml 元素常](../../../language-reference/xml-literals/xml-element-literal.md)值。  
  
## <a name="rules"></a>規則  

 Visual Basic 中的元素或屬性的本機名稱必須遵守下列規則。  
  
- 它可以從命名空間開始。 其開頭必須是字母字元或底線 (`_`) 。  
  
- 它必須只包含字母字元、十進位數、底線、句點 (. ) 和連字號 ( ) 。  
  
- 長度不得超過1024個字元。  
  
- 名稱中出現的冒號表示命名空間分界。 因此，您只能使用冒號來指定特定名稱的 XML 命名空間。  
  
 此外，您應該遵循下列指導方針。  
  
- XML 1.0 規格會針對任何大小寫變化，保留開頭為 "XML" 字串的所有名稱。 因此，請勿將這些名稱用於元素和屬性名稱。  
  
### <a name="name-length-guidelines"></a>名稱長度指導方針  

 實際上，名稱應該越短越好，同時仍然清楚地識別元素的本質。 這可提升程式碼的可讀性，並減少行長度和原始程式檔大小。  
  
 不過，您的名稱不應太短，因為它不會充分描述元素或程式碼使用它的方式。 這對您的程式碼可讀性相當重要。 如果有其他人嘗試瞭解它，或您想要在撰寫後很長一段時間，則適當的元素名稱可以節省時間。  
  
## <a name="case-sensitivity-in-names"></a>名稱中的區分大小寫  

 XML 元素名稱會區分大小寫。 這表示當 Visual Basic 編譯器比較以字母大小寫不同的兩個名稱時，會將它們視為不同的名稱。 例如，它會將 `ABC` 和 `abc` 視為參考不同的元素。  
  
## <a name="xml-namespaces"></a>XML 命名空間  

 建立 XML 元素常值時，您可以為專案名稱指定 XML 命名空間前置詞。 如需詳細資訊，請參閱 [XML 元素常](../../../language-reference/xml-literals/xml-element-literal.md)值。  
  
## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中建立 XML](creating-xml.md)
- [XML 元素常值](../../../language-reference/xml-literals/xml-element-literal.md)
