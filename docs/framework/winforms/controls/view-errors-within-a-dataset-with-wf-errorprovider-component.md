---
title: 如何：使用 Windows Form ErrorProvider 元件檢視資料集錯誤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: f00d874f2a4afcea3498a64fe946a93c83eb7b9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537082"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>如何：使用 Windows Form ErrorProvider 元件檢視資料集錯誤
您可以使用 Windows Form<xref:System.Windows.Forms.ErrorProvider>元件來檢視資料集或其他資料來源內的資料行錯誤。 如<xref:System.Windows.Forms.ErrorProvider>元件，以在表單上顯示資料錯誤不一定要與控制項直接關聯。 它是繫結至資料來源，它可以顯示錯誤圖示旁邊繫結至相同的資料來源的任何控制項。  
  
> [!NOTE]
>  如果您變更錯誤提供者的<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>和<xref:System.Windows.Forms.ErrorProvider.DataMember%2A>屬性在執行階段，您應該使用<xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A>方法，以避免發生衝突。  
  
### <a name="to-display-data-errors"></a>若要顯示的資料錯誤  
  
1.  將元件繫結至資料表中的特定資料行。  
  
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
  
2.  設定<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>表單的屬性。  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3.  將目前記錄的位置設定包含資料行發生錯誤的資料列。  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [ErrorProvider 元件概觀](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [操作說明：使用 Windows Forms ErrorProvider 元件顯示表單驗證的錯誤圖示](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
