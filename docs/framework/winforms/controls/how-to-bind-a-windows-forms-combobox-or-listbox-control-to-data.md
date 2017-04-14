---
title: "如何：將 Windows Form ComboBox 或 ListBox 控制項繫結至資料 | Microsoft Docs"
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
  - "繫結控制項, 下拉式方塊"
  - "下拉式方塊, 資料繫結"
  - "ComboBox 控制項 [Windows Form], 資料繫結"
  - "資料 [Windows Form], 繫結至控制項"
  - "資料繫結, 下拉式方塊"
  - "資料繫結控制項, Windows Form"
  - "清單方塊, 資料繫結"
  - "ListBox 控制項 [Windows Form], 資料繫結"
  - "Windows Form 控制項, 資料繫結"
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：將 Windows Form ComboBox 或 ListBox 控制項繫結至資料
您可以將 <xref:System.Windows.Forms.ComboBox> 和 <xref:System.Windows.Forms.ListBox> 繫結至資料，以執行像是瀏覽資料庫中的資料、輸入新資料或是編輯現有資料這類工作。  
  
### 若要繫結 ComboBox 或 ListBox 控制項  
  
1.  將 `DataSource`  屬性設為資料來源物件。  可能的資料來源包括繫結至資料的 <xref:System.Windows.Forms.BindingSource>、資料的資料表 \(Data Table\)、資料檢視、資料集、資料檢視管理員、陣列或任何會實作 <xref:System.Collections.IList> 介面的類別。  如需詳細資訊，請參閱 [Windows Form 支援的資料來源](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)。  
  
2.  如果您要繫結至資料表，請將 `DisplayMember`  屬性設定為資料來源中的資料行名稱。  
  
     \-或\-  
  
     如果您要繫結至 <xref:System.Collections.IList>，請將顯示成員設定為清單中的型別之公用屬性。  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
  
    ```  
  
    > [!NOTE]
    >  如果您繫結至沒有實作 <xref:System.ComponentModel.IBindingList> 介面的資料來源 \(例如 <xref:System.Collections.ArrayList>\)，則當資料來源更新時，繫結控制項的資料將不會更新。  例如，如果您將下拉式方塊繫結至 <xref:System.Collections.ArrayList>，而且資料加入至 <xref:System.Collections.ArrayList>，則這些新項目將不會出現在下拉式方塊中。  然而，您可以呼叫繫結控制項的 <xref:System.Windows.Forms.BindingContext> 類別的執行個體上的 <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> 和 <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> 方法強制下拉式方塊更新。  
  
## 請參閱  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 [Windows Form 資料繫結](../../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [資料繫結和 Windows Form](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [用來列出選項的 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)