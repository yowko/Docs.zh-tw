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
ms.openlocfilehash: 5b1f8ccc402f7f5928a33f434664b0f28d108e6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61828612"
---
# <a name="declared-element-names-visual-basic"></a>宣告項目名稱 (Visual Basic)
每個宣告的項目有一個名稱，也稱為*識別碼*，這是程式碼會使用來參考它。  
  
## <a name="rules"></a>規則  
 在 Visual Basic 中的項目名稱必須遵守下列規則：  
  
-   它必須以字母字元或底線開頭 (`_`)。  
  
-   它必須只包含字母字元、 十進位數字和底線。  
  
-   如果它是以底線開頭，它必須包含至少一個字母字元或十進位數字。  
  
-   它不能超過 1023年個字元。  
  
 長度超過 1023年個字元的限制也適用於整個字串的完整限定名稱，例如`outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`。  
  
 下列範例顯示一些有效的項目名稱。  
  
 `aB123__45`  
  
 `_567`  
  
 下列範例顯示一些無效的項目名稱。 第一個包含只底線、 十進位數字，以開頭的第二個和第三個包含無效的字元 （$）。  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  項目名稱開頭為底線 (`_`) 不屬於[Language Independence and Language-independent Components](../../../../standard/language-independence-and-language-independent-components.md) （cls） 標準，所以符合 CLS 標準的程式碼無法使用定義這類名稱的元件。 不過，在項目名稱中的任何其他位置中的底線是符合 CLS 標準。  
  
### <a name="name-length-guidelines"></a>名稱長度指導方針  
 事實上，您的名稱應該越短越好時仍可清楚識別的項目。 這可改善程式碼的可讀性，並減少列長度和原始程式檔的大小。  
  
 相反地，您的名稱不應該簡短，它不會適當地描述項目所代表的意義和您的程式碼如何使用它。 這是很重要的程式碼的可讀性。 如果其他人嘗試了解它，或您自行查看它很長的時間之後您所撰寫,，適合的項目名稱可以節省花一些時間。  
  
## <a name="escaped-names"></a>逸出的名稱  
 一般而言，項目名稱必須符合任何所保留的關鍵字 Visual Basic 中，這類`Case`或`Friend`。 不過，您可以定義*逸出名稱*，這加上括號 (`[ ]`)。 逸出的名稱可以比對任何 Visual Basic 關鍵字，因為在方括號移除任何模稜兩可。 當您稍後在程式碼中參考名稱時，也可以使用方括號。  
  
 一般情況下，您應該使用逸出的名稱時，才：  
  
-   移轉您的程式碼，從舊版的 Visual Basic，未保留關鍵字做為欄位名稱。或  
  
-   您正在使用不會保留指定的關鍵字是另一種語言撰寫的程式碼。  
  
 否則，您應該考慮重新命名項目，如果其名稱與關鍵字相衝突。 整合式的開發環境 (IDE) 提供簡單的方法，若要這樣做。 如需詳細資訊，請參閱 <<c0> [ 重構](/visualstudio/vb-ide/refactoring-vb)。  
  
## <a name="case-sensitivity-in-names"></a>在名稱中的區分大小寫  
 在 Visual Basic 中的項目名稱不區分大小寫。 這表示，當編譯器會比較兩個字母大小寫不同的名稱，它會將它們解譯成相同的名稱。 例如，它會將 `ABC` 和 `abc` 視為相同的宣告元素。  
  
 不過，common language runtime (CLR) 會使用區分大小寫的繫結。 因此，當您產生一個組件或 DLL 並讓其他組件使用時，您的名稱將會區分大小寫。 例如，如果您使用名為 `ABC`的元素來定義類別，而其他組件透過 Common Language Runtime 使用您的類別，則這些組件必須以 `ABC`來表示該元素。 如果您之後在重新編譯您的類別，而且變更的項目名稱，以`abc`，則使用您的類別的組件無法再存取該元素。 因此，當您發行組件的更新版本時，不應該變更任何公用元素的字母大小寫。  
  
## <a name="names-and-locales"></a>名稱和地區設定  
 比較名稱與地區設定無關。 如果兩個名稱符合在一個地區設定中，保證在所有地區設定中比對。  
  
## <a name="see-also"></a>另請參閱

- [宣告項目](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [陳述式](../../../../visual-basic/language-reference/statements/index.md)
