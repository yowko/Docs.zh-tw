---
title: "宣告的 XML 項目和屬性 (Visual Basic) 的名稱 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ed8ecf69170acf9745a4038975e7e3421722d52d
ms.lasthandoff: 03/13/2017

---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>宣告的 XML 項目和屬性的名稱 (Visual Basic)
本主題提供[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML 項目和 XML 常值中的屬性命名指導方針。  您可以在 XML 常值，指定區域名稱或完整的名稱。 限定的名稱是由 XML 命名空間前置詞、 冒號與本機名稱所組成。 如需 XML 命名空間前置詞的詳細資訊，請參閱[XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## <a name="rules"></a>規則  
 項目或屬性中的本機名稱[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]必須遵守下列規則。  
  
-   它可以開始使用命名空間。 它必須以字母字元或底線 (`_`)。  
  
-   它必須包含僅字母字元、 十進位數字、 底線、 句號 （.） 和連字號 （-）。  
  
-   它不能超過 1024 個字元長。  
  
-   出現在名稱中的冒號表示命名空間的分界。 因此，您可以使用冒號，只是用來指定特定名稱的 XML 命名空間。  
  
 此外，您應該遵守下列指導方針。  
  
-   XML 1.0 規格會保留所有名稱開頭為"xml"，任何大小寫變化的字串。 因此，請勿使用這些元素的名稱和屬性名稱。  
  
### <a name="name-length-guidelines"></a>名稱長度方針  
 事實上，名稱應該盡量縮短但仍可清楚識別的項目。 這可改善程式碼的可讀性，並減少線條長度和原始程式檔的大小。  
  
 不過，您的名稱不應該過短，無法正確地描述項目或程式碼使用它。 這是很重要的程式碼的可讀性。 如果有人試圖了解它，或您自己想要在您撰寫之後很長的時間，適當的項目名稱可以節省時間。  
  
## <a name="case-sensitivity-in-names"></a>在 名稱區分大小寫  
 XML 項目名稱會區分大小寫。 這表示當[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器比較兩個不同的字母大小寫的名稱，它會將它們解譯為不同的名稱。 比方說，它可解譯`ABC`和`abc`解釋為個別項目。  
  
## <a name="xml-namespaces"></a>XML 命名空間  
 在建立 XML 項目常值時，您可以指定 XML 命名空間前置詞的項目名稱。 如需詳細資訊，請參閱[XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
