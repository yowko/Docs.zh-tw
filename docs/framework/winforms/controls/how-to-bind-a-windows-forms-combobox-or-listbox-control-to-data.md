---
title: HOW TO：將 Windows Forms ComboBox 或 ListBox 控制項繫結至資料
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
ms.openlocfilehash: b869898a20008343b6c6cbe4bc7e399fc86fb232
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054012"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="54198-102">HOW TO：將 Windows Forms ComboBox 或 ListBox 控制項繫結至資料</span><span class="sxs-lookup"><span data-stu-id="54198-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="54198-103">您可以繫結<xref:System.Windows.Forms.ComboBox>和<xref:System.Windows.Forms.ListBox>資料，以執行工作，例如瀏覽資料庫中的資料，以在輸入新的資料，或編輯現有的資料。</span><span class="sxs-lookup"><span data-stu-id="54198-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="54198-104">將 ComboBox 或 ListBox 控制項繫結</span><span class="sxs-lookup"><span data-stu-id="54198-104">To bind a ComboBox or ListBox control</span></span>  
  
1. <span data-ttu-id="54198-105">設定`DataSource`資料來源物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="54198-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="54198-106">可能的資料來源包括<xref:System.Windows.Forms.BindingSource>管理員、 陣列或任何實作類別的繫結至資料、 資料表、 資料檢視、 資料集，資料檢視<xref:System.Collections.IList>介面。</span><span class="sxs-lookup"><span data-stu-id="54198-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="54198-107">如需詳細資訊，請參閱 <<c0> [ 支援的 Windows Form 資料來源](../data-sources-supported-by-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="54198-107">For more information, see [Data Sources Supported by Windows Forms](../data-sources-supported-by-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="54198-108">如果您要繫結至資料表，將設定`DisplayMember`屬性設為資料來源中的資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="54198-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="54198-109">\-或-</span><span class="sxs-lookup"><span data-stu-id="54198-109">\- or -</span></span>  
  
     <span data-ttu-id="54198-110">如果您要繫結<xref:System.Collections.IList>，顯示成員設定為清單中類型的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="54198-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
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
    >  <span data-ttu-id="54198-111">如果您繫結至資料來源未實作<xref:System.ComponentModel.IBindingList>介面，例如<xref:System.Collections.ArrayList>，更新資料來源時，將不會更新繫結的控制項的資料。</span><span class="sxs-lookup"><span data-stu-id="54198-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="54198-112">例如，如果您有下拉式方塊繫結至<xref:System.Collections.ArrayList>而且資料會加入至<xref:System.Collections.ArrayList>，這些新的項目不會出現在下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="54198-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="54198-113">不過，您可以在其中強制下拉式方塊，藉由呼叫更新<xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A>並<xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A>執行個體上的方法<xref:System.Windows.Forms.BindingContext>控制項所繫結類別。</span><span class="sxs-lookup"><span data-stu-id="54198-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54198-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54198-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="54198-115">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="54198-115">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="54198-116">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="54198-116">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="54198-117">用來列出選項的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="54198-117">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
