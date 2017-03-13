---
title: "Imports Statement (.NET Namespace and Type) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Imports"
  - "imports"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declared element names [Visual Basic], qualification"
  - "imports [Visual Basic]"
  - "Imports statement [Visual Basic]"
  - "aliases [Visual Basic], Imports statement"
  - "container elements [Visual Basic]"
  - "namespaces [Visual Basic], importing"
  - "Imports statement [Visual Basic], syntax"
  - "import aliases [Visual Basic]"
  - "aliases [Visual Basic], import"
  - "declared elements [Visual Basic], container elements"
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
caps.latest.revision: 40
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 40
---
# Imports Statement (.NET Namespace and Type)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

允許不使用命名空間限定性條件來參考型別名稱。  
  
## 語法  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`aliasname`|選擇項。  「*匯入別名*」或名稱，程式碼可依據此名稱參考 `namespace` 而非完整限定字串。  請參閱[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`namespace`|必要項。  要匯入之命名空間的完整名稱。  可以是任何巢狀層級的命名空間字串。|  
|`element`|選擇項。  在命名空間中宣告的程式設計項目名稱。  可以是任何容器項目。|  
  
## 備註  
 `Imports` 陳述式允許直接參考特定命名空間中包含的型別。  
  
 ：您可以提供單一命名空間名稱或巢狀命名空間的字串。  每個巢狀命名空間都會以句號 \(`.`\) 隔開下一個較高層級的命名空間，如下列範例所示。  
  
 `Imports System.Collections.Generic`  
  
 每個原始程式檔 \(Source File\) 都能包含任何數目的 `Imports` 陳述式。  這些陳述式必須在選項宣告之後 \(例如 `Option Strict` 陳述式\)，而且它們必須在任何程式設計項目宣告之前 \(例如 `Module` 或 `Class` 陳述式\)。  
  
 您只能在檔案層級中使用 `Imports`。  這表示匯入的宣告內容必須是原始程式檔，而且不能是命名空間、類別、結構、模組、介面、程序或區塊。  
  
 請注意，`Imports` 陳述式無法讓您的專案使用其他專案和組件中的項目。  匯入不會取代設定參考的功能。  它只是不再需要限定專案已經可以使用的名稱。  如需詳細資訊，請參閱[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的＜匯入包含的項目＞。  
  
> [!NOTE]
>  您可以使用 [專案設計工具，參考頁 \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)，定義隱含 `Imports` 陳述式。  如需詳細資訊，請參閱 [如何：加入或移除匯入的命名空間 \(Visual Basic\)](../Topic/How%20to:%20Add%20or%20Remove%20Imported%20Namespaces%20\(Visual%20Basic\).md)。  
  
## 匯入別名  
 「*匯入別名*」\(Import Alias\) 會定義命名空間或型別的別名。  當您需要使用在一個或多個命名空間內宣告且具有相同名稱的項目時，匯入別名將會很有用。  如需詳細資訊和範例，請參閱[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的＜限定項目名稱＞。  
  
 您不應該在模組層級以相同的名稱將成員宣告為 `aliasname`。  如果您這樣做，Visual Basic 編譯器 \(Compiler\) 只會對宣告的成員使用 `aliasname`，而不再將它辨識為匯入別名。  
  
 雖然用來宣告匯入別名的語法與用來匯入 XML 命名空間前置字元的語法類似，但結果卻不同。  匯入別名可以做為程式碼中的運算式使用，但 XML 命名空間前置字元只能做為 XML 常值或 XML 軸屬性 \(Property\) 中的限定項目或屬性 \(Attribute\) 名稱前置字元使用。  
  
### 項目名稱  
 如果您提供 `element`，它一定代表「*容器項目*」\(Container Element\)，也就是可以包含其他項目的程式設計項目。  容器項目包含類別、結構、模組、介面和列舉型別 \(Enumeration\)。  
  
 要讓 `Imports` 陳述式使項目範圍變成可用的，需視您是否有指定 `element` 而定。  如果您只指定 `namespace`，所有該命名空間唯一具名的成員及該命名空間中容器項目的成員，都可以在沒有限定性條件下使用。  如果您指定 `namespace` 和 `element`，則只有該項目的成員可以在沒有限定性條件下使用。  
  
## 範例  
 下列範例會使用 <xref:System.IO.DirectoryInfo> 類別傳回 C:\\ 目錄中的所有資料夾。  
  
 程式碼檔案的頂端沒有 `Imports` 陳述式。  因此 `DirectoryInfo`、<xref:System.Text.StringBuilder> 和 <xref:Microsoft.VisualBasic.ControlChars.CrLf> 參考都是透過命名空間完整限定。  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## 範例  
 下列範例包含參考的命名空間的 `Imports` 陳述式。  因此型別不需要以命名空間完整限定。  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## 範例  
 下列範例包含建立所參考命名空間之別名的 `Imports` 陳述式。  型別是以別名所限定。  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## 範例  
 下列範例包含建立所參考型別之別名的 `Imports` 陳述式。  別名會用於指定型別。  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## 請參閱  
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)