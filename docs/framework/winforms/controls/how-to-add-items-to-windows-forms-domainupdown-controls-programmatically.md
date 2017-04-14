---
title: "如何：以程式設計的方式將項目加入至 Windows Form DomainUpDown 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DomainUpDown 控制項 [Windows Form], 加入項目至"
  - "微調按鈕控制項, 加入項目"
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：以程式設計的方式將項目加入至 Windows Form DomainUpDown 控制項
您可以在程式碼中將項目加入至 Windows Form <xref:System.Windows.Forms.DomainUpDown> 控制項。  呼叫 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> 類別的 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> 或 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> 方法，將項目加入控制項的 <xref:System.Windows.Forms.DomainUpDown.Items%2A> 屬性。  <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> 方法會將項目加入至集合的尾端，而 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> 方法則會將項目加入指定的位置。  
  
### 若要加入新項目  
  
1.  使用 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> 方法將項目加入至項目清單的尾端。  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     \-或\-  
  
2.  使用 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> 方法將項目插入清單的指定位置。  
  
    ```vb  
    ' Inserts an item at the third position in the list  
    DomainUpDown1.Items.Insert(2, "rice")  
  
    ```  
  
    ```csharp  
    // Inserts an item at the third position in the list  
    domainUpDown1.Items.Insert(2, "rice");  
  
    ```  
  
    ```cpp  
    // Inserts an item at the third position in the list  
    domainUpDown1->Items->Insert(2, "rice");  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.DomainUpDown>   
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=fullName>   
 <xref:System.Collections.ArrayList.Insert%2A?displayProperty=fullName>   
 [DomainUpDown 控制項](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)   
 [DomainUpDown 控制項概觀](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)