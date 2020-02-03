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
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="d9c57-102">如何：使用 Windows Form ErrorProvider 元件檢視資料集錯誤</span><span class="sxs-lookup"><span data-stu-id="d9c57-102">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="d9c57-103">您可以使用 Windows Forms <xref:System.Windows.Forms.ErrorProvider> 元件來查看資料集或其他資料來源中的資料行錯誤。</span><span class="sxs-lookup"><span data-stu-id="d9c57-103">You can use the Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to view column errors within a dataset or other data source.</span></span> <span data-ttu-id="d9c57-104">若要讓 <xref:System.Windows.Forms.ErrorProvider> 元件顯示表單上的資料錯誤，則不需要直接與控制項相關聯。</span><span class="sxs-lookup"><span data-stu-id="d9c57-104">For an <xref:System.Windows.Forms.ErrorProvider> component to display data errors on a form, it does not have to be directly associated with a control.</span></span> <span data-ttu-id="d9c57-105">一旦系結至資料來源，它就可以在系結至相同資料來源的任何控制項旁顯示錯誤圖示。</span><span class="sxs-lookup"><span data-stu-id="d9c57-105">Once it is bound to a data source, it can display an error icon next to any control that is bound to the same data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9c57-106">如果您在執行時間變更錯誤提供者的 <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> 並 <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> 屬性，您應該使用 <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> 方法來避免衝突。</span><span class="sxs-lookup"><span data-stu-id="d9c57-106">If you change the error provider's <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> and <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> properties at run time, you should use the <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> method to avoid conflicts.</span></span>  
  
### <a name="to-display-data-errors"></a><span data-ttu-id="d9c57-107">若要顯示資料錯誤</span><span class="sxs-lookup"><span data-stu-id="d9c57-107">To display data errors</span></span>  
  
1. <span data-ttu-id="d9c57-108">將元件系結至資料表中的特定資料行。</span><span class="sxs-lookup"><span data-stu-id="d9c57-108">Bind the component to a specific column within a data table.</span></span>  
  
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
  
2. <span data-ttu-id="d9c57-109">將 [<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>] 屬性設為表單。</span><span class="sxs-lookup"><span data-stu-id="d9c57-109">Set the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property to the form.</span></span>  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3. <span data-ttu-id="d9c57-110">將目前記錄的位置設定為包含資料行錯誤的資料列。</span><span class="sxs-lookup"><span data-stu-id="d9c57-110">Set the position of the current record to a row that contains a column error.</span></span>  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d9c57-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9c57-111">See also</span></span>

- [<span data-ttu-id="d9c57-112">ErrorProvider 元件概觀</span><span class="sxs-lookup"><span data-stu-id="d9c57-112">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="d9c57-113">操作說明：使用 Windows Forms ErrorProvider 元件顯示表單驗證的錯誤圖示</span><span class="sxs-lookup"><span data-stu-id="d9c57-113">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>](display-error-icons-for-form-validation-with-wf-errorprovider.md)
