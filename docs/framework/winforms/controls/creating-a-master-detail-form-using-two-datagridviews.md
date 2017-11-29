---
title: "逐步解說： 建立主從式表單使用兩個 Windows Form DataGridView 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0d213d70d6f12cb8b574f07457c1b20317670d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="1753b-102">逐步解說：使用兩個 Windows Form DataGridView 控制項建立主要/詳細表單</span><span class="sxs-lookup"><span data-stu-id="1753b-102">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="1753b-103">其中一個最常見的案例使用<xref:System.Windows.Forms.DataGridView>控制項是*主從式*表單，其中會顯示兩個資料庫資料表之間的父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="1753b-103">One of the most common scenarios for using the <xref:System.Windows.Forms.DataGridView> control is the *master/detail* form, in which a parent/child relationship between two database tables is displayed.</span></span> <span data-ttu-id="1753b-104">主要資料表中選取資料列會讓使用對應的子資料來更新詳細資料資料表。</span><span class="sxs-lookup"><span data-stu-id="1753b-104">Selecting rows in the master table causes the detail table to update with the corresponding child data.</span></span>  
  
 <span data-ttu-id="1753b-105">實作主要/詳細表單很容易使用之間的互動<xref:System.Windows.Forms.DataGridView>控制項和<xref:System.Windows.Forms.BindingSource>元件。</span><span class="sxs-lookup"><span data-stu-id="1753b-105">Implementing a master/detail form is easy using the interaction between the <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="1753b-106">在本逐步解說，您將建立使用兩個表單<xref:System.Windows.Forms.DataGridView>控制項及兩個<xref:System.Windows.Forms.BindingSource>元件。</span><span class="sxs-lookup"><span data-stu-id="1753b-106">In this walkthrough, you will build the form using two <xref:System.Windows.Forms.DataGridView> controls and two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="1753b-107">表單會顯示兩個相關 Northwind SQL Server 範例資料庫中的資料表：`Customers`和`Orders`。</span><span class="sxs-lookup"><span data-stu-id="1753b-107">The form will show two related tables in the Northwind SQL Server sample database: `Customers` and `Orders`.</span></span> <span data-ttu-id="1753b-108">當您完成時，您必須在 master 資料庫中會顯示所有客戶表單<xref:System.Windows.Forms.DataGridView>和詳細資料中所選客戶的訂單<xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="1753b-108">When you are finished, you will have a form that shows all the customers in the database in the master <xref:System.Windows.Forms.DataGridView> and all the orders for the selected customer in the detail <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
 <span data-ttu-id="1753b-109">若要為單一列出本主題中複製的程式碼，請參閱[How to： 建立主從式表單使用兩個 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)。</span><span class="sxs-lookup"><span data-stu-id="1753b-109">To copy the code in this topic as a single listing, see [How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1753b-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="1753b-110">Prerequisites</span></span>  
 <span data-ttu-id="1753b-111">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="1753b-111">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="1753b-112">Northwind SQL Server 範例資料庫的伺服器存取。</span><span class="sxs-lookup"><span data-stu-id="1753b-112">Access to a server that has the Northwind SQL Server sample database.</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="1753b-113">建立表單</span><span class="sxs-lookup"><span data-stu-id="1753b-113">Creating the form</span></span>  
  
#### <a name="to-create-a-masterdetail-form"></a><span data-ttu-id="1753b-114">若要建立主要/詳細表單</span><span class="sxs-lookup"><span data-stu-id="1753b-114">To create a master/detail form</span></span>  
  
1.  <span data-ttu-id="1753b-115">建立衍生自類別<xref:System.Windows.Forms.Form>和包含兩個<xref:System.Windows.Forms.DataGridView>控制項及兩個<xref:System.Windows.Forms.BindingSource>元件。</span><span class="sxs-lookup"><span data-stu-id="1753b-115">Create a class that derives from <xref:System.Windows.Forms.Form> and contains two <xref:System.Windows.Forms.DataGridView> controls and two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="1753b-116">下列程式碼提供基本的形式初始化，而且包含`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="1753b-116">The following code provides basic form initialization and includes a `Main` method.</span></span> <span data-ttu-id="1753b-117">如果您使用[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]設計工具來建立表單，您可以使用設計工具產生的程式碼，而不是這個程式碼，但一定要使用變數宣告中所顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="1753b-117">If you use the [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] designer to create your form, you can use the designer generated code instead of this code, but be sure to use the names shown in the variable declarations here.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  <span data-ttu-id="1753b-118">在您的表單類別定義處理資料庫連接的詳細資料中實作的方法。</span><span class="sxs-lookup"><span data-stu-id="1753b-118">Implement a method in your form's class definition for handling the detail of connecting to the database.</span></span> <span data-ttu-id="1753b-119">這個範例會使用`GetData`方法填入<xref:System.Data.DataSet>物件時，會新增<xref:System.Data.DataRelation>資料集，以及繫結物件<xref:System.Windows.Forms.BindingSource>元件。</span><span class="sxs-lookup"><span data-stu-id="1753b-119">This example uses a `GetData` method that populates a <xref:System.Data.DataSet> object, adds a <xref:System.Data.DataRelation> object to the data set, and binds the <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="1753b-120">請務必將 `connectionString` 變數設定為適用於您資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="1753b-120">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1753b-121">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="1753b-121">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="1753b-122">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="1753b-122">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="1753b-123">如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="1753b-123">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  <span data-ttu-id="1753b-124">實作您的表單的處理常式<xref:System.Windows.Forms.Form.Load>繫結的事件<xref:System.Windows.Forms.DataGridView>控制項<xref:System.Windows.Forms.BindingSource>元件並呼叫`GetData`方法。</span><span class="sxs-lookup"><span data-stu-id="1753b-124">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that binds the <xref:System.Windows.Forms.DataGridView> controls to the <xref:System.Windows.Forms.BindingSource> components and calls the `GetData` method.</span></span> <span data-ttu-id="1753b-125">下列範例包含調整大小的程式碼<xref:System.Windows.Forms.DataGridView>欄位至最適大小所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="1753b-125">The following example includes code that resizes <xref:System.Windows.Forms.DataGridView> columns to fit the displayed data.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="1753b-126">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="1753b-126">Testing the Application</span></span>  
 <span data-ttu-id="1753b-127">您現在可以測試表單，以確定其如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="1753b-127">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="1753b-128">若要測試表單</span><span class="sxs-lookup"><span data-stu-id="1753b-128">To test the form</span></span>  
  
-   <span data-ttu-id="1753b-129">編譯並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="1753b-129">Compile and run the application.</span></span>  
  
     <span data-ttu-id="1753b-130">您會看到兩個<xref:System.Windows.Forms.DataGridView>控制項，在彼此上方。</span><span class="sxs-lookup"><span data-stu-id="1753b-130">You will see two <xref:System.Windows.Forms.DataGridView> controls, one above the other.</span></span> <span data-ttu-id="1753b-131">在最上層是 northwind 客戶`Customers`資料表，並在下方是`Orders`對應至選取的客戶。</span><span class="sxs-lookup"><span data-stu-id="1753b-131">On top are the customers from the Northwind `Customers` table, and at the bottom are the `Orders` corresponding to the selected customer.</span></span> <span data-ttu-id="1753b-132">當您選取不同的資料列的上方<xref:System.Windows.Forms.DataGridView>，較低的內容<xref:System.Windows.Forms.DataGridView>據此變更。</span><span class="sxs-lookup"><span data-stu-id="1753b-132">As you select different rows in the upper <xref:System.Windows.Forms.DataGridView>, the contents of the lower <xref:System.Windows.Forms.DataGridView> change accordingly.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1753b-133">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1753b-133">Next Steps</span></span>  
 <span data-ttu-id="1753b-134">此應用程式可讓您基本的了解<xref:System.Windows.Forms.DataGridView>控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="1753b-134">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="1753b-135">您可以自訂的外觀和行為<xref:System.Windows.Forms.DataGridView>數種方式控制：</span><span class="sxs-lookup"><span data-stu-id="1753b-135">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
-   <span data-ttu-id="1753b-136">變更框線和標題的樣式。</span><span class="sxs-lookup"><span data-stu-id="1753b-136">Change border and header styles.</span></span> <span data-ttu-id="1753b-137">如需詳細資訊，請參閱[如何： 變更 Windows Form DataGridView 控制項中的格線樣式和框線](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="1753b-137">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="1753b-138">啟用或限制使用者輸入到<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="1753b-138">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1753b-139">如需詳細資訊，請參閱[如何： 防止資料列新增和刪除 Windows Form DataGridView 控制項中的](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)，和[如何： 使 Windows Form DataGridView 控制項中的資料行唯讀](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1753b-139">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="1753b-140">驗證使用者輸入，<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="1753b-140">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1753b-141">如需詳細資訊，請參閱[逐步解說： 驗證 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1753b-141">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="1753b-142">處理非常大型的資料集使用的虛擬模式。</span><span class="sxs-lookup"><span data-stu-id="1753b-142">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="1753b-143">如需詳細資訊，請參閱[逐步解說： 在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1753b-143">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="1753b-144">自訂儲存格的外觀。</span><span class="sxs-lookup"><span data-stu-id="1753b-144">Customize the appearance of cells.</span></span> <span data-ttu-id="1753b-145">如需詳細資訊，請參閱[How to： 自訂 Windows Form DataGridView 控制項中的儲存格外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)和[How to： 設定預設儲存格樣式的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1753b-145">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1753b-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1753b-146">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="1753b-147">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="1753b-147">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1753b-148">操作說明：使用兩個 Windows Forms DataGridView 控制項建立主從式表單</span><span class="sxs-lookup"><span data-stu-id="1753b-148">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)  
 [<span data-ttu-id="1753b-149">保護連線資訊</span><span class="sxs-lookup"><span data-stu-id="1753b-149">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
