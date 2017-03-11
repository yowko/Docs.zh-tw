---
title: "How to: Access Members of an Object (Visual Basic) | Microsoft Docs"
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
  - "members, accessing"
  - "object variables, accessing members"
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How to: Access Members of an Object (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

擁有參考到物件的物件變數時，您通常會想要使用該物件的成員，例如方法、屬性、欄位和事件等等。  例如建立新的 <xref:System.Windows.Forms.Form> 物件之後，您可能會想要設定它的 <xref:System.Windows.Forms.Control.Text%2A> 屬性或呼叫它的 <xref:System.Windows.Forms.Control.Focus%2A> 方法。  
  
## 存取成員  
 您可以透過參考到物件成員的變數，來存取物件的成員。  
  
#### 若要存取物件的成員  
  
-   在物件變數名稱和成員名稱之間使用成員存取運算子 \(`.`\)。  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     如果成員是 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)，則不需要變數即可存取成員。  
  
## 存取已知型別物件的成員  
 如果您可以在編譯時期確認物件的型別，則可以針對參考該物件的變數使用「*早期繫結*」\(Early Binding\)。  
  
#### 若要在編譯時期便已確認物件型別的情況下，存取物件的成員  
  
1.  宣告物件變數，使其型別符合想要指派給該變數的物件。  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form   
    ```  
  
     使用 `Option Strict On` 時，您只能將 <xref:System.Windows.Forms.Form> 物件 \(或型別衍生自 <xref:System.Windows.Forms.Form> 的物件\) 指派給 `extraForm`。  如果您定義了類別或結構，並執行 `CType` 擴展轉換將其轉換至 <xref:System.Windows.Forms.Form>，便可將該類別或結構指派給 `extraForm`。  
  
2.  在物件變數名稱和成員名稱之間使用成員存取運算子 \(`.`\)。  
  
    ```  
    extraForm.Show()  
    ```  
  
     不論 `Option Strict` 設定為何，您都可以存取 <xref:System.Windows.Forms.Form> 類別 \(Class\) 特有的所有方法和屬性。  
  
## 存取未知型別物件的成員  
 如果您無法在編譯時期確認物件的型別，則必須針對任何參考該物件的變數使用「*晚期繫結*」\(Late Binding\)。  
  
#### 若要在編譯時期無法確認物件型別的情況下，存取物件的成員  
  
1.  宣告物件變數，使其成為 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)。  \(將變數宣告為 `Object` 的方式，和將變數宣告為 <xref:System.Object?displayProperty=fullName> 一樣\)。  
  
    ```  
    Dim someControl As Object   
    ```  
  
     使用 `Option Strict On` 時，您只能存取 <xref:System.Object> 類別 \(Class\) 中已經定義的成員。  
  
2.  在物件變數名稱和成員名稱之間使用成員存取運算子 \(`.`\)。  
  
    ```  
    someControl.GetType()  
    ```  
  
     為了能夠存取您指派給物件變數的任何物件的成員，您必須設定 `Option Strict Off`。  這樣做時，編譯器 \(Compiler\) 無法保證您指派給變數的物件會公開 \(Expose\) 指定的成員。  如果物件沒有公開您想要存取的成員，就會發生 <xref:System.MemberAccessException> 例外狀況。  
  
## 請參閱  
 <xref:System.Object>   
 <xref:System.Windows.Forms.Form>   
 <xref:System.MemberAccessException>   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)