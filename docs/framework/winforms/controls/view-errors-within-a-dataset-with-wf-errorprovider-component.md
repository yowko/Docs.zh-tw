---
title: "如何：使用 Windows Form ErrorProvider 元件檢視資料集錯誤 | Microsoft Docs"
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
  - "錯誤訊息, 在資料集中檢視"
  - "ErrorProvider 元件 [Windows Form], 資料集錯誤"
  - "錯誤 [Windows Form], 資料集錯誤"
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用 Windows Form ErrorProvider 元件檢視資料集錯誤
您可以使用 Windows Form 的 <xref:System.Windows.Forms.ErrorProvider> 元件，檢視資料集或其他資料來源的資料行錯誤。  <xref:System.Windows.Forms.ErrorProvider> 元件不需要直接與控制項關聯，就能在表單中顯示資料錯誤。  當它與資料來源繫結時，可以在任何繫結至同一資料來源的控制項旁顯示錯誤圖示。  
  
> [!NOTE]
>  如果您要在執行階段變更錯誤提供者的 <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> 和 <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> 屬性，請使用 <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> 方法以避免衝突。  
  
### 若要顯示資料錯誤  
  
1.  將元件繫結至資料的資料表 \(Data Table\) 內的特定資料行。  
  
    ```vb  
    ' Assumes existence of DataSet1, DataTable1  
    TextBox1.DataBindings.Add("Text", DataSet1, "Customers.Name")  
    ErrorProvider1.DataSource = DataSet1  
    ErrorProvider1.DataMember = "Customers"  
  
    ```  
  
    ```csharp  
    // Assumes existence of DataSet1, DataTable1  
    textBox1.DataBindings.Add("Text", DataSet1, "Customers.Name");  
    errorProvider1.DataSource = DataSet1;  
    errorProvider1.DataMember = "Customers";  
  
    ```  
  
2.  將 <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> 屬性設定為表單。  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
  
    ```  
  
3.  將目前記錄的位置設定為包含資料行錯誤的資料列。  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
  
    ```  
  
## 請參閱  
 [ErrorProvider 元件概觀](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)   
 [如何：使用 Windows Form ErrorProvider 元件顯示表單驗證的錯誤圖示](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)