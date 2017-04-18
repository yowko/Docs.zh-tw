---
title: "如何：從 Windows Form DomainUpDown 控制項中移除項目 | Microsoft Docs"
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
  - "DomainUpDown 控制項 [Windows Form], 移除項目自"
  - "微調按鈕控制項, 移除項目"
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：從 Windows Form DomainUpDown 控制項中移除項目
可藉由呼叫 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> 類別的 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> 或 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> 方法，從 Windows Form <xref:System.Windows.Forms.DomainUpDown> 控制項中移除項目。  <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> 方法會移除指定的項目，<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> 方法則會按照項目的位置移除項目。  
  
### 若要移除項目  
  
-   請使用 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> 類別的 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> 方法按名稱移除項目。  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     \-或\-  
  
-   請使用 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> 方法按項目的位置移除項目。  
  
    ```vb  
    ' Removes the first item in the list.  
    DomainUpDown1.Items.RemoveAt(0)  
  
    ```  
  
    ```csharp  
    // Removes the first item in the list.  
    domainUpDown1.Items.RemoveAt(0);  
  
    ```  
  
    ```cpp  
    // Removes the first item in the list.  
    domainUpDown1->Items->RemoveAt(0);  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.DomainUpDown>   
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=fullName>   
 [DomainUpDown 控制項](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)   
 [DomainUpDown 控制項概觀](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)