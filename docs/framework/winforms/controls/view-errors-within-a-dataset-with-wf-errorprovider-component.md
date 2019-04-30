---
title: HOW TO：使用 Windows Forms ErrorProvider 元件檢視資料集錯誤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: 15fbf4a3cebef1485f0c54ace36ab88f3d4289e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962574"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="0e962-102">HOW TO：使用 Windows Forms ErrorProvider 元件檢視資料集錯誤</span><span class="sxs-lookup"><span data-stu-id="0e962-102">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="0e962-103">您可以使用 Windows Form<xref:System.Windows.Forms.ErrorProvider>元件來檢視資料集或其他資料來源內的資料行錯誤。</span><span class="sxs-lookup"><span data-stu-id="0e962-103">You can use the Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to view column errors within a dataset or other data source.</span></span> <span data-ttu-id="0e962-104">針對<xref:System.Windows.Forms.ErrorProvider>元件，以在表單上顯示資料的錯誤不一定要直接控制項相關聯。</span><span class="sxs-lookup"><span data-stu-id="0e962-104">For an <xref:System.Windows.Forms.ErrorProvider> component to display data errors on a form, it does not have to be directly associated with a control.</span></span> <span data-ttu-id="0e962-105">一旦它已繫結至資料來源，它可以顯示錯誤圖示旁邊繫結至相同的資料來源的任何控制項。</span><span class="sxs-lookup"><span data-stu-id="0e962-105">Once it is bound to a data source, it can display an error icon next to any control that is bound to the same data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e962-106">如果您變更的錯誤提供者<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>並<xref:System.Windows.Forms.ErrorProvider.DataMember%2A>在執行階段的屬性，您應該使用<xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A>方法，以避免發生衝突。</span><span class="sxs-lookup"><span data-stu-id="0e962-106">If you change the error provider's <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> and <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> properties at run time, you should use the <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> method to avoid conflicts.</span></span>  
  
### <a name="to-display-data-errors"></a><span data-ttu-id="0e962-107">若要顯示資料錯誤</span><span class="sxs-lookup"><span data-stu-id="0e962-107">To display data errors</span></span>  
  
1. <span data-ttu-id="0e962-108">將元件的繫結至資料表中的特定資料行。</span><span class="sxs-lookup"><span data-stu-id="0e962-108">Bind the component to a specific column within a data table.</span></span>  
  
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
  
2. <span data-ttu-id="0e962-109">設定<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>屬性到表單。</span><span class="sxs-lookup"><span data-stu-id="0e962-109">Set the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property to the form.</span></span>  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3. <span data-ttu-id="0e962-110">將目前記錄的位置，設定包含資料行發生錯誤的資料列。</span><span class="sxs-lookup"><span data-stu-id="0e962-110">Set the position of the current record to a row that contains a column error.</span></span>  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0e962-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e962-111">See also</span></span>

- [<span data-ttu-id="0e962-112">ErrorProvider 元件概觀</span><span class="sxs-lookup"><span data-stu-id="0e962-112">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="0e962-113">如何：表單驗證，使用 Windows Forms ErrorProvider 元件顯示錯誤圖示</span><span class="sxs-lookup"><span data-stu-id="0e962-113">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>](display-error-icons-for-form-validation-with-wf-errorprovider.md)
