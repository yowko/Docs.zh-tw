---
title: "宣告項目名稱 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declared elements, case sensitivity
- names, Visual Basic rules
- naming conventions
- element names
- declared elements, identifiers
- declarations, elements
- declared elements, valid names
- '[] escape characters [Visual Basic]'
- names, elements
- declaration statements, declared elements
- declaring elements
- identifiers, declared elements
- case sensitivity, declared element names
- escape characters
- names, declared elements
- declared elements, about declared elements
- escaped names
- declared elements, names
- names, naming conventions
- identifiers, elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: 27
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
ms.openlocfilehash: 56ac0684e5176f33aa6f9600f20d9fe3fcf09416
ms.lasthandoff: 03/13/2017

---
# <a name="declared-element-names-visual-basic"></a>宣告項目名稱 (Visual Basic)
每個宣告的項目都有名稱，也稱為*識別碼*，這是程式碼使用來參考它。  
  
## <a name="rules"></a>規則  
 中的元素名稱[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]必須遵守下列規則︰  
  
-   它必須以字母字元或底線 (`_`)。  
  
-   它只能包含字母字元、 十進位數字和底線。  
  
-   如果它是以底線開頭，它必須包含至少一個字母字元或十進位數字。  
  
-   它不能超過 1023年個字元。  
  
 1023 個字元的長度限制也適用於整個字串的完整名稱，例如`outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`。  
  
 下列範例顯示一些有效的項目名稱。  
  
 `aB123__45`  
  
 `_567`  
  
 下列範例顯示一些無效的項目名稱。 第一個包含僅底線、 十進位數字，開頭為第二個和第三個包含無效的字元 （$）。  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  項目名稱開頭是底線 (`_`) 是不屬於[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)(CLS)，所以符合 CLS 標準的程式碼不能使用的元件，定義這類名稱。 不過，任何其他項目名稱中的位置底線是符合 CLS 標準。  
  
### <a name="name-length-guidelines"></a>名稱長度方針  
 事實上，您的名稱應該盡量縮短但仍可清楚識別的項目。 這可改善程式碼的可讀性，並減少線條長度和原始程式檔的大小。  
  
 相反地，您的名稱不應該過短，無法正確地描述項目所代表的意義和您的程式碼如何使用它。 這是很重要的程式碼的可讀性。 如果有人試圖了解它，或您自己想要在您撰寫之後很長的時間，適當的項目名稱可以節省大量的時間。  
  
## <a name="escaped-names"></a>逸出的名稱  
 通常，項目名稱必須符合任何保留的關鍵字[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，例如`Case`或`Friend`。 不過，您可以定義*逸出名稱*，這以括弧括住 (`[ ]`)。 逸出的名稱比對任何[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]關鍵字，因為括號移除任何模稜兩可。 當您稍後在程式碼中參考名稱時，也可以使用方括號。  
  
 一般情況下，您應該使用逸出的名稱時，才︰  
  
-   從舊版移轉您的程式碼[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，沒有不使用保留關鍵字做為名稱; 或  
  
-   您正在使用不會保留指定的關鍵字是另一種語言撰寫的程式碼。  
  
 否則，您應該考慮重新命名項目，如果其名稱與關鍵字衝突。 整合式的開發環境 (IDE) 提供簡單的方法。 如需詳細資訊，請參閱[重整](https://docs.microsoft.com/visualstudio/vb-ide/refactoring-vb)。  
  
## <a name="case-sensitivity-in-names"></a>在 名稱區分大小寫  
 中的項目名稱[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]不區分大小寫。 這表示，當編譯器比較兩個字母大小寫不同的名稱，它會將它們解譯為相同的名稱。 例如，它會將 `ABC` 和 `abc` 視為相同的宣告元素。  
  
 不過，common language runtime (CLR) 會使用區分大小寫的繫結。 因此，當您產生一個組件或 DLL 並讓其他組件使用時，您的名稱將會區分大小寫。 例如，如果您使用名為 `ABC`的元素來定義類別，而其他組件透過 Common Language Runtime 使用您的類別，則這些組件必須以 `ABC`來表示該元素。 如果您後續重新編譯類別，並變更的項目名稱`abc`，則使用您的類別的組件就無法再存取該項目。 因此，當您發行組件的更新版本時，不應該變更任何公用元素的字母大小寫。  
  
## <a name="names-and-locales"></a>名稱和地區設定  
 名稱的比較與地區設定無關。 如果兩個名稱符合一個地區，他們保證符合所有地區設定。  
  
## <a name="see-also"></a>另請參閱  
 [宣告項目](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)   
 [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [宣告項目參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [陳述式](../../../../visual-basic/language-reference/statements/index.md)
