---
title: "在 Visual Basic 中為變數進行疑難排解 | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "疑難排解 [Visual Basic], 變數"
  - "變數 [Visual Basic], 疑難排解"
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# 在 Visual Basic 中為變數進行疑難排解
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

本頁列出在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中使用變數時可能發生的一些常見問題。  
  
## 無法存取物件的成員  
 如果您的程式碼嘗試存取物件的屬性或方法，可能會發生兩種錯誤結果：  
  
-   如果您宣告物件變數屬於特定類型，然後參考該類型未定義的成員，編譯器可能會產生錯誤訊息。  
  
-   當指派給物件變數的物件未公開您的程式碼嘗試存取的成員時，就會發生執行階段 <xref:System.MemberAccessException>。 如果變數屬於 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)，您也可能會在成員不是 `Public` 的情況下收到此例外狀況。 這是因為晚期繫結只允許存取 `Public` 成員。  
  
 當 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) 將類型檢查設定為 `On` 時，物件變數只能存取您用以宣告之類別的方法和屬性。 下列範例將說明這點。  
  
 [!CODE [VbVbalrStatements#49](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrStatements#49)]  
  
 [!code-vb[VbVbalrVariables#2](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]  
  
 在此範例中，`p` 只能使用 <xref:System.Object> 類別本身的成員，其並未包含 `Left` 屬性。 另一方面，已宣告 `q` 屬於 <xref:System.Windows.Forms.Label> 類型，因此它可以使用 <xref:System.Windows.Forms> 命名空間中 <xref:System.Windows.Forms.Label> 類別的所有方法和屬性。  
  
### 正確方法  
 若要能夠存取特定類別之物件的所有成員，請盡可能宣告物件變數屬於該類別的類型。 如果您無法執行此作業 \(例如假設您在編譯時間不知道物件類型\)，您必須將 `Option Strict` 設定為 `Off`，以宣告變數屬於 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)。 這樣就能將任何類型的物件指派給變數，您也應該採取步驟確認目前指派的物件屬於可接受的類型。 您可以使用 [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) 來做出此判斷。  
  
## 其他元件無法存取您的變數  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 名稱*不區分大小寫*。 如果兩個名稱只有字母大小寫不同，則編譯器會將它們解譯成相同的名稱。 例如，它會將 `ABC` 和 `abc` 視為相同的宣告元素。  
  
 不過，Common Language Runtime \(CLR\) 使用*區分大小寫* 的繫結。 因此，當您產生一個組件或 DLL 並讓其他組件使用時，您的名稱將會區分大小寫。 例如，如果您使用名為 `ABC` 的元素來定義類別，而其他組件透過 Common Language Runtime 使用您的類別，則這些組件必須以 `ABC` 來表示該元素。 如果您隨後重新編譯類別，並將元素的名稱變更為 `abc`，則其他使用此類別的組件就無法再存取該元素。 因此，當您發行組件的更新版本時，不應該變更任何公用元素的字母大小寫。  
  
 如需詳細資訊，請參閱[Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md)。  
  
### 正確方法  
 若要讓其他元件能夠存取您的變數，請將其名稱視為區分大小寫。 當您正在測試類別或模組時，請確定其他組件繫結至預定的變數。 一旦發行元件後，請勿修改現有的變數名稱，包括變更其大小寫。  
  
## 使用錯誤的變數  
 當您有多個同名的變數時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會嘗試解析該名稱的每個參考。 如果變數具有不同的範圍，則編譯器會用最小的範圍來解析宣告的參考。 如果範圍相同，則解析會失敗，且編譯器會發出錯誤信號。 如需詳細資訊，請參閱[References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
### 正確方法  
 避免使用具有相同名稱但不同範圍的變數。 如果您想要使用其他組件或專案，請盡可能避免使用這些外部元件所定義的任何名稱。 如果您有多個同名的變數時，請務必限定它的每個參考。 如需詳細資訊，請參閱[References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
## 請參閱  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [How to: Access Members of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [How to: Determine What Type an Object Variable Refers To](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)