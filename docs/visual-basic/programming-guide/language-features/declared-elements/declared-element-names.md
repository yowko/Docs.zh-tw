---
title: "Declared Element Names (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declared elements, case sensitivity"
  - "names, Visual Basic rules"
  - "naming conventions"
  - "element names"
  - "declared elements, identifiers"
  - "declarations, elements"
  - "declared elements, valid names"
  - "[] escape characters [Visual Basic]"
  - "names, elements"
  - "declaration statements, declared elements"
  - "declaring elements"
  - "identifiers, declared elements"
  - "case sensitivity, declared element names"
  - "escape characters"
  - "names, declared elements"
  - "declared elements, about declared elements"
  - "escaped names"
  - "declared elements, names"
  - "names, naming conventions"
  - "identifiers, elements"
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Declared Element Names (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

每個宣告項目都有名稱，亦稱作「*識別項*」\(Identifier\)，可供程式碼參考之用。  
  
## 規則  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的項目名稱必須遵守下列規則：  
  
-   必須以字母字元或底線 \(`_`\) 開頭。  
  
-   只能包含字母字元、十進位數字和底線。  
  
-   如果是以底線開頭，必須含有至少一個字母順序字元或十進位數字。  
  
-   長度不可超過 1023 個字元。  
  
 1023 個字元的長度限制也適用於完整名稱 \(Qualified Name\) 的整個字串，例如 `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`。  
  
 下列範例顯示幾個有效的項目名稱。  
  
 `aB123__45`  
  
 `_567`  
  
 下列範例顯示幾個無效的項目名稱。  第一個名稱僅包含底線，第二個以十進位數字開頭，而第三個包含無效字元 \($\)。  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  由於以底線 \(`_`\) 開頭的項目名稱不屬於 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 的一部分，所以符合 CLS 標準的程式碼無法使用定義這類名稱的元件。  不過，在項目名稱中的任何其他位置使用底線則符合 CLS 標準。  
  
### 名稱長度方針  
 依實用性而言，您的名稱應該盡可能簡短，但仍可清楚識別項目。  這可以提升程式碼的可讀性、縮短行的長度和減少原始程式檔 \(Source File\) 大小。  
  
 另一方面，您的名稱也不可短到無法充分描述項目代表的意義，以及它在程式碼中的用途。  這對程式碼的可讀性十分重要。  如果他人嘗試了解您的程式碼，或是您自己在撰寫之後很久再回頭查閱，適當的項目名稱可以節省大量的閱讀時間。  
  
## 逸出名稱  
 一般來說，項目名稱不可與 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 保留的關鍵字相同，例如 `Case` 或 `Friend`。  但是您可定義一個放在中括號 \(`[ ]`\) 內的「*逸出名稱*」\(Escaped Name\)。  逸出名稱可與任何 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 關鍵字相同，因為該括號可解決模稜兩可 \(Ambiguity\) 的問題。  當您稍後在程式碼中參考該名稱時也必須加上中括號。  
  
 一般而言，只有在下列情況中才需要使用逸出名稱：  
  
-   移轉自舊版本 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 的程式碼，而該版本並未將您使用的名稱保留為關鍵字；或  
  
-   使用以其他語言撰寫的程式碼，而指定關鍵字在這種語言中並未被保留。  
  
 此外，項目名稱與關鍵字產生衝突時，您應考慮重新命名該項目。  整合式開發環境 \(IDE\) 提供您簡便的更名方式。  如需詳細資訊，請參閱 [重構和重新命名對話方塊](../../../../visual-basic/developing-apps/using-ide/refactoring-and-rename-dialog-box.md)。  
  
## 名稱區分大小寫  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的項目名稱不區分大小寫。  這表示當編譯器比較兩個只有大小寫不同的名稱時，會將它們當做相同的名稱來解譯。  例如，編譯器會將 `ABC` 和 `abc` 視為相同的宣告項目。  
  
 然而，Common Language Runtime \(CLR\) 使用區分大小寫的繫結。  因此當您產生一個組件 \(Assembly\) 或 DLL 讓其他組件使用時，您的名稱將會區分大小寫。  例如，如果您使用名為 `ABC` 的項目來定義類別，而其他組件透過 Common Language Runtime 使用您的類別，則它們必須以 `ABC` 來表示該項目。  如果您隨後重新編譯類別，並將項目名稱更改為 `abc`，則其他使用這個類別的組件就無法再存取該項目。  因此，當您公佈組件的更新版本時，不應該更改任何公用項目的字母大小寫。  
  
## 名稱和地區設定  
 名稱比較和地區設定無關。  如果兩個名稱在一個地區設定中相符，它們一定在所有的地區設定中都相符。  
  
## 請參閱  
 [Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)   
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Statements](../../../../visual-basic/language-reference/statements/index.md)