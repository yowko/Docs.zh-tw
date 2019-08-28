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
ms.openlocfilehash: 8a1b4869588c8dd030cf6276969063ec99b79e33
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046590"
---
# <a name="declared-element-names-visual-basic"></a>宣告項目名稱 (Visual Basic)
每個宣告的專案都有名稱, 也稱為「識別碼」 ( *identifier*), 這就是程式碼用來參考它的專案。  
  
## <a name="rules"></a>規則  
 Visual Basic 中的元素名稱必須遵守下列規則:  
  
- 其開頭必須是字母字元或底線 (`_`)。  
  
- 它必須只包含字母字元、十進位數和底線。  
  
- 如果開頭是底線, 它必須包含至少一個字母字元或十進位數。  
  
- 長度不得超過1023個字元。  
  
 1023個字元的長度限制也適用于完整名稱的整個字串, 例如`outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`。  
  
 下列範例顯示一些有效的元素名稱。  
  
 `aB123__45`  
  
 `_567`  
  
 下列範例顯示一些不正確元素名稱。 第一個只包含底線, 第二個開頭為十進位數, 而第三個包含不正確字元 ($)。  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> 以底線 (`_`) 開頭的元素名稱不是[語言獨立性和與語言無關的元件](../../../../standard/language-independence-and-language-independent-components.md)(CLS) 的一部分, 因此符合 CLS 標準的程式碼無法使用定義這類名稱的元件。 不過, 元素名稱中任何其他位置的底線都符合 CLS 標準。  
  
### <a name="name-length-guidelines"></a>名稱長度指導方針  
 實際上, 您的名稱應該越短越好, 同時仍能清楚地識別元素的本質。 這可以改善程式碼的可讀性, 並縮短行長度和原始程式檔大小。  
  
 另一方面, 您的名稱應該不會太短, 因為它不會適當地描述專案所代表的內容, 以及您的程式碼使用它的方式。 這對於您的程式碼可讀性很重要。 如果有人嘗試瞭解它, 或如果您在撰寫完之後, 想要很長的時間查看它, 適當的元素名稱可以節省大量的時間。  
  
## <a name="escaped-names"></a>轉義的名稱  
 一般來說, 專案名稱不能符合 Visual Basic 所保留的任何關鍵字, 例如`Case`或。 `Friend` 不過, 您可以定義以方括弧 (`[ ]`) 括住的*轉義名稱*。 轉義的名稱可以符合任何 Visual Basic 關鍵字, 因為方括弧會移除任何不明確的。 當您稍後在程式碼中參考名稱時, 也會使用括弧。  
  
 一般而言, 只有在下列情況下, 才應該使用轉義名稱:  
  
- 您的程式碼已從舊版的 Visual Basic 進行遷移, 但未保留做為名稱使用的關鍵字;或  
  
- 您正在使用以另一種語言撰寫的程式碼, 其中指定的關鍵字不是保留的。  
  
 否則, 如果元素的名稱與關鍵字衝突, 您應該考慮重新命名專案。 整合式開發環境 (IDE) 提供簡單的方法來執行此動作。 如需詳細資訊, 請參閱[重構](/visualstudio/vb-ide/refactoring-vb)。  
  
## <a name="case-sensitivity-in-names"></a>名稱區分大小寫  
 Visual Basic 中的元素名稱不區分大小寫。 這表示當編譯器只比較字母大小寫不同的兩個名稱時, 它會將它們解讀為相同的名稱。 例如，它會將 `ABC` 和 `abc` 視為相同的宣告元素。  
  
 不過, common language runtime (CLR) 使用區分大小寫的系結。 因此，當您產生一個組件或 DLL 並讓其他組件使用時，您的名稱將會區分大小寫。 例如，如果您使用名為 `ABC`的元素來定義類別，而其他組件透過 Common Language Runtime 使用您的類別，則這些組件必須以 `ABC`來表示該元素。 如果您接著重新編譯類別, 並將專案的名稱變更`abc`為, 則其他使用您類別的元件將無法再存取該元素。 因此，當您發行組件的更新版本時，不應該變更任何公用元素的字母大小寫。  
  
## <a name="names-and-locales"></a>名稱和地區設定  
 名稱的比較與地區設定無關。 如果兩個名稱符合一個地區設定, 則會保證所有地區設定的相符。  
  
## <a name="see-also"></a>另請參閱

- [宣告項目](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [陳述式](../../../../visual-basic/language-reference/statements/index.md)
