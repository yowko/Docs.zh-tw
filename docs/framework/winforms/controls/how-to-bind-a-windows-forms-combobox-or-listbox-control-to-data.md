---
title: 將 ComboBox 或 ListBox 控制項系結至資料
description: 瞭解如何將 Windows Forms ComboBox 和 ListBox 系結至資料，以執行工作，例如流覽資料庫中的資料、輸入新資料，或編輯現有的資料。
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
ms.openlocfilehash: 0c07dc90ddc91061c5f34b5a237082cb444e89d9
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324066"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="659dc-103">如何：將 Windows Form ComboBox 或 ListBox 控制項繫結至資料</span><span class="sxs-lookup"><span data-stu-id="659dc-103">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="659dc-104">您可以將和系結 <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ListBox> 至資料，以執行工作，例如流覽資料庫中的資料、輸入新資料，或編輯現有的資料。</span><span class="sxs-lookup"><span data-stu-id="659dc-104">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="659dc-105">若要系結 ComboBox 或 ListBox 控制項</span><span class="sxs-lookup"><span data-stu-id="659dc-105">To bind a ComboBox or ListBox control</span></span>  
  
1. <span data-ttu-id="659dc-106">將 `DataSource` 屬性設定為數據源物件。</span><span class="sxs-lookup"><span data-stu-id="659dc-106">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="659dc-107">可能的資料來源包括系結 <xref:System.Windows.Forms.BindingSource> 至資料、資料表、資料檢視、dataset、資料檢視管理員、陣列，或任何可執行介面的類別 <xref:System.Collections.IList> 。</span><span class="sxs-lookup"><span data-stu-id="659dc-107">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="659dc-108">如需詳細資訊，請參閱[Windows Forms 支援的資料來源](../data-sources-supported-by-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="659dc-108">For more information, see [Data Sources Supported by Windows Forms](../data-sources-supported-by-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="659dc-109">如果您要系結至資料表，請將 `DisplayMember` 屬性設定為數據源中的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="659dc-109">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="659dc-110">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="659dc-110">\- or -</span></span>  
  
     <span data-ttu-id="659dc-111">如果您要系結至 <xref:System.Collections.IList> ，請將 [顯示成員] 設定為清單中類型的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="659dc-111">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
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
    > <span data-ttu-id="659dc-112">如果您系結至不會執行介面的資料來源（ <xref:System.ComponentModel.IBindingList> 例如），則在 <xref:System.Collections.ArrayList> 更新資料來源時，將不會更新繫結控制項的資料。</span><span class="sxs-lookup"><span data-stu-id="659dc-112">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="659dc-113">例如，如果您有系結至的下拉式方塊， <xref:System.Collections.ArrayList> 而且資料已加入至 <xref:System.Collections.ArrayList> ，這些新專案將不會出現在下拉式方塊中。</span><span class="sxs-lookup"><span data-stu-id="659dc-113">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="659dc-114">不過，您可以在控制項所系結的 <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> 類別實例上呼叫和方法，強制更新下拉式方塊 <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> <xref:System.Windows.Forms.BindingContext> 。</span><span class="sxs-lookup"><span data-stu-id="659dc-114">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="659dc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="659dc-115">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="659dc-116">Windows Form 資料繫結</span><span class="sxs-lookup"><span data-stu-id="659dc-116">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="659dc-117">資料繫結和 Windows Form</span><span class="sxs-lookup"><span data-stu-id="659dc-117">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="659dc-118">用來列出選項的 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="659dc-118">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
