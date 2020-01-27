---
title: 使用 ErrorProvider 元件來查看資料集內的錯誤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: 8c2155bf288db89b5d53567738fd399b915d50b6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745461"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>如何：使用 Windows Form ErrorProvider 元件檢視資料集錯誤
您可以使用 Windows Forms <xref:System.Windows.Forms.ErrorProvider> 元件來查看資料集或其他資料來源中的資料行錯誤。 若要讓 <xref:System.Windows.Forms.ErrorProvider> 元件顯示表單上的資料錯誤，則不需要直接與控制項相關聯。 一旦系結至資料來源，它就可以在系結至相同資料來源的任何控制項旁顯示錯誤圖示。  
  
> [!NOTE]
> 如果您在執行時間變更錯誤提供者的 <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> 並 <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> 屬性，您應該使用 <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> 方法來避免衝突。  
  
### <a name="to-display-data-errors"></a>若要顯示資料錯誤  
  
1. 將元件系結至資料表中的特定資料行。  
  
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
  
2. 將 [<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>] 屬性設為表單。  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3. 將目前記錄的位置設定為包含資料行錯誤的資料列。  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a>請參閱

- [ErrorProvider 元件概觀](errorprovider-component-overview-windows-forms.md)
- [操作說明：使用 Windows Forms ErrorProvider 元件顯示表單驗證的錯誤圖示](display-error-icons-for-form-validation-with-wf-errorprovider.md)
