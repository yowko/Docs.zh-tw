---
title: 宣告項目名稱 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 2f48f885b66f99ecc8c6c7e13fea7e75f0e3d24a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="declared-element-names-visual-basic"></a>宣告項目名稱 (Visual Basic)
每個宣告的項目都有名稱，也稱為*識別碼*，這是程式碼會使用來參考它。  
  
## <a name="rules"></a>規則  
 在 Visual Basic 中的元素名稱必須遵守下列規則：  
  
-   它必須以字母字元或底線開頭 (`_`)。  
  
-   它只能包含英數字元、 十進位數字和底線。  
  
-   如果它是以底線開頭，它必須包含至少一個字母字元或十進位數字。  
  
-   它不得為長度超過 1023 個字元。  
  
 1023 個字元的長度限制也適用於整個字串的完整限定名稱，例如`outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`。  
  
 下列範例顯示一些有效的項目名稱。  
  
 `aB123__45`  
  
 `_567`  
  
 下列範例示範一些無效的項目名稱。 第一個包含只底線、 十進位數字，開頭為第二個和第三個包含無效的字元 （$）。  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  項目名稱以底線開頭 (`_`) 不屬於[語言獨立性以及與語言無關的元件](../../../../standard/language-independence-and-language-independent-components.md)（cls） 標準，所以符合 CLS 標準的程式碼不能使用的元件，定義這類名稱。 不過，在項目名稱中的其他任何位置底線是符合 CLS 標準。  
  
### <a name="name-length-guidelines"></a>名稱長度指導方針  
 事實上，您的名稱應該越短越好但仍可清楚識別的項目。 這可改善程式碼的可讀性，並減少線條長度和原始程式檔的大小。  
  
 相反地，您的名稱不應該短，無法適當地描述項目所代表的意義和您的程式碼如何使用它。 這是很重要的程式碼的可讀性。 如果其他人嘗試了解它，或您自己想要在您撰寫之後很長的時間，適當的項目名稱可以節省相當多的時間。  
  
## <a name="escaped-names"></a>逸出的名稱  
 通常，項目名稱必須符合任何所保留的關鍵字 Visual Basic 中，例如`Case`或`Friend`。 不過，您可以定義*逸出名稱*，這以方括號 (`[ ]`)。 逸出的名稱可以比對任何 Visual Basic 關鍵字，在方括號會移除任何模稜兩可。 當您稍後在程式碼中參考名稱時，也會使用方括號。  
  
 一般情況下，您應該使用逸出的名稱時，才：  
  
-   您的程式碼移轉自舊版的 Visual Basic 沒有不使用保留關鍵字做為名稱。或  
  
-   您正在使用不會保留給定的關鍵字是另一種語言撰寫的程式碼。  
  
 否則，您應該考慮重新命名項目，如果其名稱與關鍵字衝突。 整合式的開發環境 (IDE) 提供簡單的方法。 如需詳細資訊，請參閱[重構](/visualstudio/vb-ide/refactoring-vb)。  
  
## <a name="case-sensitivity-in-names"></a>在名稱中的區分大小寫  
 在 Visual Basic 中的項目名稱不區分大小寫。 這表示，當編譯器比較兩個字母大小寫不同的名稱，它會將它們解譯成相同的名稱。 例如，它會將 `ABC` 和 `abc` 視為相同的宣告元素。  
  
 不過，common language runtime (CLR) 使用區分大小寫的繫結。 因此，當您產生一個組件或 DLL 並讓其他組件使用時，您的名稱將會區分大小寫。 例如，如果您使用名為 `ABC`的元素來定義類別，而其他組件透過 Common Language Runtime 使用您的類別，則這些組件必須以 `ABC`來表示該元素。 如果您隨後重新編譯類別，並變更的項目名稱以`abc`，則使用您的類別的組件就無法再存取該元素。 因此，當您發行組件的更新版本時，不應該變更任何公用元素的字母大小寫。  
  
## <a name="names-and-locales"></a>名稱和地區設定  
 比較名稱與地區設定無關。 如果兩個名稱符合一個地區設定中，保證在所有地區設定中比對。  
  
## <a name="see-also"></a>另請參閱  
 [宣告項目](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [陳述式](../../../../visual-basic/language-reference/statements/index.md)
