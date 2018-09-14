---
title: 如何：使用 Windows Form BindingSource 元件排序和篩選 ADO.NET 資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: 932d30d356225d88d7ef149561cc4c5cc8ac4dd0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45517433"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="0185d-102">如何：使用 Windows Form BindingSource 元件排序和篩選 ADO.NET 資料</span><span class="sxs-lookup"><span data-stu-id="0185d-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="0185d-103">排序和篩選功能，您可以公開<xref:System.Windows.Forms.BindingSource>透過控制<xref:System.Windows.Forms.BindingSource.Sort%2A>和<xref:System.Windows.Forms.BindingSource.Filter%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0185d-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="0185d-104">您可以套用簡單排序的基礎資料來源時<xref:System.ComponentModel.IBindingList>，您可以套用的篩選和進階排序的資料來源時<xref:System.ComponentModel.IBindingListView>。</span><span class="sxs-lookup"><span data-stu-id="0185d-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="0185d-105"><xref:System.Windows.Forms.BindingSource.Sort%2A>屬性需要標準[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]語法： 字串，表示資料來源中的資料行的名稱後面加上`ASC`或`DESC`來指出是否應該以遞增或遞減順序排序清單。</span><span class="sxs-lookup"><span data-stu-id="0185d-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="0185d-106">您可以設定進階排序，或使用逗號分隔符號隔開每個資料行的多重資料行排序。</span><span class="sxs-lookup"><span data-stu-id="0185d-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="0185d-107"><xref:System.Windows.Forms.BindingSource.Filter%2A>屬性會採用字串運算式。</span><span class="sxs-lookup"><span data-stu-id="0185d-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0185d-108">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="0185d-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="0185d-109">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="0185d-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="0185d-110">如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="0185d-110">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="0185d-111">若要篩選使用 BindingSource 的資料</span><span class="sxs-lookup"><span data-stu-id="0185d-111">To filter data with the BindingSource</span></span>  
  
-   <span data-ttu-id="0185d-112">設定<xref:System.Windows.Forms.BindingSource.Filter%2A>屬性，以您想要的運算式。</span><span class="sxs-lookup"><span data-stu-id="0185d-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="0185d-113">在下列程式碼範例中，運算式會是資料行名稱，後面接著您要的資料行的值。</span><span class="sxs-lookup"><span data-stu-id="0185d-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="0185d-114">使用 BindingSource 的資料進行排序</span><span class="sxs-lookup"><span data-stu-id="0185d-114">To sort data with the BindingSource</span></span>  
  
1.  <span data-ttu-id="0185d-115">設定<xref:System.Windows.Forms.BindingSource.Sort%2A>屬性設為資料行名稱，您想要後面`ASC`或`DESC`表示遞增或遞減順序。</span><span class="sxs-lookup"><span data-stu-id="0185d-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2.  <span data-ttu-id="0185d-116">請以逗號分隔多個資料行。</span><span class="sxs-lookup"><span data-stu-id="0185d-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="0185d-117">範例</span><span class="sxs-lookup"><span data-stu-id="0185d-117">Example</span></span>  
 <span data-ttu-id="0185d-118">下列程式碼範例會載入資料至 Northwind 範例資料庫的 Customers 資料表中<xref:System.Windows.Forms.DataGridView>控制項，並篩選並排序顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="0185d-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0185d-119">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0185d-119">Compiling the Code</span></span>  
 <span data-ttu-id="0185d-120">若要執行此範例中，貼上程式碼包含表單的表單<xref:System.Windows.Forms.BindingSource>名為`BindingSource1`並<xref:System.Windows.Forms.DataGridView>名為`dataGridView1`。</span><span class="sxs-lookup"><span data-stu-id="0185d-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="0185d-121">處理<xref:System.Windows.Forms.Form.Load>事件的形式和呼叫`InitializeSortedFilteredBindingSource`load 事件處理常式方法中。</span><span class="sxs-lookup"><span data-stu-id="0185d-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0185d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0185d-122">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
 <xref:System.Windows.Forms.BindingSource.Filter%2A>  
 [<span data-ttu-id="0185d-123">如何：安裝範例資料庫</span><span class="sxs-lookup"><span data-stu-id="0185d-123">How to: Install Sample Databases</span></span>](https://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)  
 [<span data-ttu-id="0185d-124">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="0185d-124">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
