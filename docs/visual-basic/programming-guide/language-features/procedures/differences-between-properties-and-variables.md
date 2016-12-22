---
title: "Differences Between Properties and Variables in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "property values"
  - "variables [Visual Basic]"
  - "Visual Basic code, procedures"
  - "values, properties"
  - "variables [Visual Basic], definition"
  - "Visual Basic code, variables"
  - "Visual Basic code, properties"
  - "properties [Visual Basic], values"
  - "properties [Visual Basic], defined"
  - "variables [Visual Basic], and properties"
  - "properties [Visual Basic], and variables"
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Differences Between Properties and Variables in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

變數和屬性都代表可存取的值。  然而，儲存區和實作會有所不同。  
  
## 變數  
 「*變數*」\(Variable\) 會直接對應到記憶體位置。  您可以使用單一宣告陳述式來定義變數。  變數可以是「*區域變數*」\(Local Variable\) \(定義在程序內，且只可在該程序內使用\)，或者也可以是「*成員變數*」\(Member Variable\) \(定義在模組、類別或結構內，而不在任何程序內\)。  成員變數也稱為「*欄位*」\(Field\)。  
  
## 屬性  
 「*屬性*」\(Property\) 是定義在模組、類別或結構上的資料項目。  您可以使用 `Property` 和 `End Property` 陳述式間的程式碼區塊來定義屬性。  程式碼區塊包含 `Get` 程序、`Set` 程序，或是兩者皆含。  這些程序稱為「*屬性程序*」\(Property Procedure\) 或「*屬性存取子*」\(Property Accessor\)。  除了擷取或儲存屬性值之外，它們也可執行自訂動作 \(例如，更新存取計數器\)。  
  
## 差異點  
 下表會顯示變數和屬性間的一些重要差異點。  
  
|差異點|變數|屬性|  
|---------|--------|--------|  
|宣告|單一宣告陳述式|程式碼區塊中的一連串陳述式|  
|實作|單一儲存區位置|可執行的程式碼 \(屬性程序\)|  
|儲存區|直接與變數值產生關聯|一般會有內部儲存區，不可在屬性的包含類別或模組外部使用<br /><br /> 屬性值可能是以預存項目 <sup>1</sup> 的形式存在，也可能不存在|  
|可執行的程式碼|None|至少必須有一個程序|  
|讀取和寫入存取權|讀取\/寫入或唯讀|讀取\/寫入、唯讀或唯寫|  
|自訂動作 \(除了接受或傳回值外\)|不可能|可當成設定或擷取屬性值的一部分來執行|  
  
 <sup>1</sup> 與變數不同，屬性值不可直接對應到儲存區的單一項目。  基於便利性或安全性，可將儲存區分割成數個片段，或用加密形式來儲存該值。  在這些情況下，`Get` 程序會組譯這些片段，或解密預存值，而 `Set` 程序會將新的值加密，或將它分割為構成儲存區。  屬性值可能是短暫的 \(像每天的時間\)，在這種情況下，`Get` 程序會在每次存取該屬性時，立即計算它。  
  
## 請參閱  
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [How to: Create a Property](../Topic/How%20to:%20Create%20a%20Property%20\(Visual%20Basic\).md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Call a Property Procedure](../Topic/How%20to:%20Call%20a%20Property%20Procedure%20\(Visual%20Basic\).md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)