---
title: 作法：使用 Windows Forms ErrorProvider 元件檢視資料集錯誤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: 3dbd2ccca607869a6f28bc5b3bd1c9f0769db9f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950074"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>作法：使用 Windows Forms ErrorProvider 元件檢視資料集錯誤
您可以使用 Windows Forms <xref:System.Windows.Forms.ErrorProvider>元件來查看資料集或其他資料來源中的資料行錯誤。 若要讓元件顯示表單上的資料錯誤, 則不需要直接與控制項相關聯。 <xref:System.Windows.Forms.ErrorProvider> 一旦系結至資料來源, 它就可以在系結至相同資料來源的任何控制項旁顯示錯誤圖示。  
  
> [!NOTE]
> 如果您在執行時間變更錯誤<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>提供<xref:System.Windows.Forms.ErrorProvider.DataMember%2A>者的和屬性<xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> , 您應該使用方法來避免衝突。  
  
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
  
2. <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>將屬性設定為表單。  
  
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
  
## <a name="see-also"></a>另請參閱

- [ErrorProvider 元件概觀](errorprovider-component-overview-windows-forms.md)
- [如何：使用 Windows Forms ErrorProvider 元件顯示表單驗證的錯誤圖示](display-error-icons-for-form-validation-with-wf-errorprovider.md)
