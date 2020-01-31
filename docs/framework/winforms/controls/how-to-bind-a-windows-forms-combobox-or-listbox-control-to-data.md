---
title: 將 ComboBox 或 ListBox 控制項系結至資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
ms.openlocfilehash: 99d9b53b32d6faae888b134d4ed486980c05a75b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742042"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="8391a-102">如何：將 Windows Form ComboBox 或 ListBox 控制項繫結至資料</span><span class="sxs-lookup"><span data-stu-id="8391a-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="8391a-103">您可以將 <xref:System.Windows.Forms.ComboBox> 和 <xref:System.Windows.Forms.ListBox> 系結至資料，以執行工作，例如流覽資料庫中的資料、輸入新資料，或編輯現有的資料。</span><span class="sxs-lookup"><span data-stu-id="8391a-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="8391a-104">若要系結 ComboBox 或 ListBox 控制項</span><span class="sxs-lookup"><span data-stu-id="8391a-104">To bind a ComboBox or ListBox control</span></span>  
  
1. <span data-ttu-id="8391a-105">將 [`DataSource`] 屬性設定為 [資料來源物件]。</span><span class="sxs-lookup"><span data-stu-id="8391a-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="8391a-106">可能的資料來源包括系結至資料的 <xref:System.Windows.Forms.BindingSource>、資料表、資料檢視、dataset、資料檢視管理員、陣列，或任何可執行 <xref:System.Collections.IList> 介面的類別。</span><span class="sxs-lookup"><span data-stu-id="8391a-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="8391a-107">如需詳細資訊，請參閱[Windows Forms 支援的資料來源](../data-sources-supported-by-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="8391a-107">For more information, see [Data Sources Supported by Windows Forms](../data-sources-supported-by-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="8391a-108">如果您要系結至資料表，請將 `DisplayMember` 屬性設定為數據源中的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="8391a-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="8391a-109">\-或-</span><span class="sxs-lookup"><span data-stu-id="8391a-109">\- or -</span></span>  
  
     <span data-ttu-id="8391a-110">如果您要系結至 <xref:System.Collections.IList>，請將 [顯示成員] 設定為清單中類型的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="8391a-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
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
    > <span data-ttu-id="8391a-111">如果您系結至不會執行 <xref:System.ComponentModel.IBindingList> 介面的資料來源（例如 <xref:System.Collections.ArrayList>），當資料來源更新時，將不會更新繫結控制項的資料。</span><span class="sxs-lookup"><span data-stu-id="8391a-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="8391a-112">例如，如果您有一個下拉式方塊系結至 <xref:System.Collections.ArrayList> 並將資料加入至 <xref:System.Collections.ArrayList>，這些新的專案就不會出現在下拉式方塊中。</span><span class="sxs-lookup"><span data-stu-id="8391a-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="8391a-113">不過，您可以在控制項所系結的 <xref:System.Windows.Forms.BindingContext> 類別實例上呼叫 <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> 和 <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> 方法，強制更新下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="8391a-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8391a-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8391a-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="8391a-115">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="8391a-115">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="8391a-116">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8391a-116">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="8391a-117">用來列出選項的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="8391a-117">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
