---
title: "如何：在 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項中存取特定的項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "CheckedListBox 控制項 [Windows Form], 存取項目"
  - "下拉式方塊, 存取項目"
  - "ComboBox 控制項 [Windows Form], 存取項目"
  - "清單方塊, 存取項目"
  - "ListBox 控制項 [Windows Form], 存取項目"
  - "ListBox 控制項 [Windows Form], 傳回項目資訊"
ms.assetid: 1216742f-bcf9-4ff8-8a62-d7c9053c2b96
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：在 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項中存取特定的項目
在 Windows Form 下拉式方塊、清單方塊或選取的清單方塊中存取指定的項目是一項基本工作。  您可利用程式設計方式決定指定位置的清單內容。  
  
### 若要存取指定項目  
  
1.  使用指定項目的索引來查詢 `Items`  集合：  
  
    ```vb  
    Private Function GetItemText(i As Integer) As String  
       ' Return the text of the item using the index:  
       Return ComboBox1.Items(i).ToString  
    End Function  
  
    ```  
  
    ```csharp  
    private string GetItemText(int i)  
    {  
       // Return the text of the item using the index:  
       return (comboBox1.Items[i].ToString());  
    }  
  
    ```  
  
    ```cpp  
    private:  
       String^ GetItemText(int i)  
       {  
          // Return the text of the item using the index:  
          return (comboBox1->Items->Item[i]->ToString());  
       }  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms.CheckedListBox>   
 [用來列出選項的 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)