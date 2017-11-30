---
title: "宣告的 XML 項目和屬性的名稱 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 846a028e076873d1978f751fdb70e93c7c6a81af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>宣告的 XML 項目和屬性的名稱 (Visual Basic)
本主題提供[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]XML 元素和屬性在 XML 常值命名指導方針。  您可以在 XML 常值，指定區域名稱或完整的名稱。 限定的名稱是由 XML 命名空間前置詞、 冒號和本機名稱所組成。 如需有關 XML 命名空間前置詞的詳細資訊，請參閱[XML 元素常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## <a name="rules"></a>規則  
 項目或屬性中的本機名稱[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]必須遵守下列規則。  
  
-   它可以開始與命名空間。 它必須以字母字元或底線開頭 (`_`)。  
  
-   它必須包含只字母字元、 十進位數字、 底線、 句號 （.） 和連字號 （-）。  
  
-   它不能超過 1024 個字元長。  
  
-   出現在名稱中的冒號表示命名空間區分。 因此，您可以使用冒號，只是用來指定特定名稱的 XML 命名空間。  
  
 此外，您應遵守下列指導方針。  
  
-   XML 1.0 規格會保留所有名稱開頭為"xml"，任何大小寫變化的字串。 因此，請勿使用這些名稱，您的項目和屬性名稱。  
  
### <a name="name-length-guidelines"></a>名稱長度指導方針  
 事實上，名稱應該短越好，但仍可清楚識別的項目。 這可改善程式碼的可讀性，並減少線條長度和原始程式檔的大小。  
  
 不過，您的名稱不應該短，無法適當地描述項目，或您的程式碼如何使用它。 這是很重要的程式碼的可讀性。 如果其他人嘗試了解它，或您自己想要在您撰寫之後很長的時間，適當的項目名稱可以節省時間。  
  
## <a name="case-sensitivity-in-names"></a>在名稱中的區分大小寫  
 XML 項目名稱會區分大小寫。 這表示當[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器比較兩個名稱只有字母大小寫不同，它會將它們解譯為不同的名稱。 例如，它可解譯`ABC`和`abc`視為參考到分隔項目。  
  
## <a name="xml-namespaces"></a>XML 命名空間  
 在建立 XML 項目常值時，您可以指定的項目名稱的 XML 命名空間前置詞。 如需詳細資訊，請參閱[XML 元素常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
