---
title: 逐步解說：使用兩個 Windows Forms DataGridView 控制項建立主版詳細資料表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
ms.openlocfilehash: 4212c7223aca6a5e7de3189d5f6b2757453cc438
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046088"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="3f976-102">逐步解說：使用兩個 Windows Forms DataGridView 控制項建立主從式表單</span><span class="sxs-lookup"><span data-stu-id="3f976-102">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>

<span data-ttu-id="3f976-103">使用<xref:System.Windows.Forms.DataGridView>此控制項的其中一個最常見案例是*主要/詳細資料*形式, 其中會顯示兩個資料庫資料表之間的父/子關聯性。</span><span class="sxs-lookup"><span data-stu-id="3f976-103">One of the most common scenarios for using the <xref:System.Windows.Forms.DataGridView> control is the *master/detail* form, in which a parent/child relationship between two database tables is displayed.</span></span> <span data-ttu-id="3f976-104">選取主資料表中的資料列, 會使詳細資料表以對應的子資料進行更新。</span><span class="sxs-lookup"><span data-stu-id="3f976-104">Selecting rows in the master table causes the detail table to update with the corresponding child data.</span></span>

<span data-ttu-id="3f976-105">使用<xref:System.Windows.Forms.DataGridView> 控制項<xref:System.Windows.Forms.BindingSource>和元件之間的互動, 可以輕鬆地執行主要/詳細表單。</span><span class="sxs-lookup"><span data-stu-id="3f976-105">Implementing a master/detail form is easy using the interaction between the <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="3f976-106">在此逐步解說中, 您將使用兩個<xref:System.Windows.Forms.DataGridView>控制項和兩<xref:System.Windows.Forms.BindingSource>個元件來建立表單。</span><span class="sxs-lookup"><span data-stu-id="3f976-106">In this walkthrough, you will build the form using two <xref:System.Windows.Forms.DataGridView> controls and two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="3f976-107">表單會顯示 Northwind SQL Server 範例資料庫中的兩個相關資料表: `Customers`和`Orders`。</span><span class="sxs-lookup"><span data-stu-id="3f976-107">The form will show two related tables in the Northwind SQL Server sample database: `Customers` and `Orders`.</span></span> <span data-ttu-id="3f976-108">當您完成時, 您將會有一個表單, 顯示主<xref:System.Windows.Forms.DataGridView>資料庫中的所有客戶, 以及所選客戶在詳細資料<xref:System.Windows.Forms.DataGridView>中的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="3f976-108">When you are finished, you will have a form that shows all the customers in the database in the master <xref:System.Windows.Forms.DataGridView> and all the orders for the selected customer in the detail <xref:System.Windows.Forms.DataGridView>.</span></span>

<span data-ttu-id="3f976-109">若要將此主題中的程式碼複製為單一清單，請參閱[如何：使用兩個 Windows Forms DataGridView 控制項](create-a-master-detail-form-using-two-datagridviews.md)建立主要/詳細表單。</span><span class="sxs-lookup"><span data-stu-id="3f976-109">To copy the code in this topic as a single listing, see [How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls](create-a-master-detail-form-using-two-datagridviews.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f976-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="3f976-110">Prerequisites</span></span>

<span data-ttu-id="3f976-111">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="3f976-111">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="3f976-112">具有 Northwind SQL Server 範例資料庫之伺服器的存取權。</span><span class="sxs-lookup"><span data-stu-id="3f976-112">Access to a server that has the Northwind SQL Server sample database.</span></span>

## <a name="creating-the-form"></a><span data-ttu-id="3f976-113">建立表單</span><span class="sxs-lookup"><span data-stu-id="3f976-113">Creating the form</span></span>

#### <a name="to-create-a-masterdetail-form"></a><span data-ttu-id="3f976-114">若要建立主要/詳細資料表單</span><span class="sxs-lookup"><span data-stu-id="3f976-114">To create a master/detail form</span></span>

1. <span data-ttu-id="3f976-115">建立衍生自<xref:System.Windows.Forms.Form>的類別, 並包含兩<xref:System.Windows.Forms.DataGridView>個控制項和<xref:System.Windows.Forms.BindingSource>兩個元件。</span><span class="sxs-lookup"><span data-stu-id="3f976-115">Create a class that derives from <xref:System.Windows.Forms.Form> and contains two <xref:System.Windows.Forms.DataGridView> controls and two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="3f976-116">下列程式碼提供基本表單初始化, 並`Main`包含方法。</span><span class="sxs-lookup"><span data-stu-id="3f976-116">The following code provides basic form initialization and includes a `Main` method.</span></span> <span data-ttu-id="3f976-117">如果您使用 Visual Studio 設計工具來建立表單, 您可以使用設計工具產生的程式碼, 而不是這段程式碼, 但請務必使用此處變數宣告中所顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="3f976-117">If you use the Visual Studio designer to create your form, you can use the designer generated code instead of this code, but be sure to use the names shown in the variable declarations here.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]

2. <span data-ttu-id="3f976-118">在表單的類別定義中執行方法, 以處理連接至資料庫的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3f976-118">Implement a method in your form's class definition for handling the detail of connecting to the database.</span></span> <span data-ttu-id="3f976-119">這個範例會使用`GetData`方法來<xref:System.Data.DataSet>填入物件、將<xref:System.Data.DataRelation>物件加入<xref:System.Windows.Forms.BindingSource>至資料集, 以及系結元件。</span><span class="sxs-lookup"><span data-stu-id="3f976-119">This example uses a `GetData` method that populates a <xref:System.Data.DataSet> object, adds a <xref:System.Data.DataRelation> object to the data set, and binds the <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="3f976-120">請務必將 `connectionString` 變數設定為適用於您資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="3f976-120">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="3f976-121">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="3f976-121">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="3f976-122">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="3f976-122">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="3f976-123">如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="3f976-123">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]

3. <span data-ttu-id="3f976-124">執行表單<xref:System.Windows.Forms.Form.Load>事件的處理常式, <xref:System.Windows.Forms.DataGridView>以將控制項系結至<xref:System.Windows.Forms.BindingSource>元件並呼叫`GetData`方法。</span><span class="sxs-lookup"><span data-stu-id="3f976-124">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that binds the <xref:System.Windows.Forms.DataGridView> controls to the <xref:System.Windows.Forms.BindingSource> components and calls the `GetData` method.</span></span> <span data-ttu-id="3f976-125">下列範例所包含的程式碼<xref:System.Windows.Forms.DataGridView>會調整資料行的大小, 以符合顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="3f976-125">The following example includes code that resizes <xref:System.Windows.Forms.DataGridView> columns to fit the displayed data.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]

## <a name="testing-the-application"></a><span data-ttu-id="3f976-126">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="3f976-126">Testing the Application</span></span>

<span data-ttu-id="3f976-127">您現在可以測試表單, 以確定它會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="3f976-127">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="3f976-128">測試表單</span><span class="sxs-lookup"><span data-stu-id="3f976-128">To test the form</span></span>

- <span data-ttu-id="3f976-129">編譯並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f976-129">Compile and run the application.</span></span>

  <span data-ttu-id="3f976-130">您會看到兩<xref:System.Windows.Forms.DataGridView>個控制項, 其中一個是在另一個上方。</span><span class="sxs-lookup"><span data-stu-id="3f976-130">You will see two <xref:System.Windows.Forms.DataGridView> controls, one above the other.</span></span> <span data-ttu-id="3f976-131">最上面是 Northwind `Customers`資料表的客戶, 而底部則是對應到所選客戶的。 `Orders`</span><span class="sxs-lookup"><span data-stu-id="3f976-131">On top are the customers from the Northwind `Customers` table, and at the bottom are the `Orders` corresponding to the selected customer.</span></span> <span data-ttu-id="3f976-132">當您選取上方<xref:System.Windows.Forms.DataGridView>的不同資料列時, 會據以變更較低<xref:System.Windows.Forms.DataGridView>的內容。</span><span class="sxs-lookup"><span data-stu-id="3f976-132">As you select different rows in the upper <xref:System.Windows.Forms.DataGridView>, the contents of the lower <xref:System.Windows.Forms.DataGridView> change accordingly.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3f976-133">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3f976-133">Next Steps</span></span>

<span data-ttu-id="3f976-134">此應用程式可讓您對<xref:System.Windows.Forms.DataGridView>控制項的功能有基本瞭解。</span><span class="sxs-lookup"><span data-stu-id="3f976-134">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="3f976-135">您可以透過數種方式自訂<xref:System.Windows.Forms.DataGridView>控制項的外觀和行為:</span><span class="sxs-lookup"><span data-stu-id="3f976-135">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>

- <span data-ttu-id="3f976-136">變更框線和標題樣式。</span><span class="sxs-lookup"><span data-stu-id="3f976-136">Change border and header styles.</span></span> <span data-ttu-id="3f976-137">如需詳細資訊，請參閱[如何：變更 Windows Forms DataGridView 控制項](change-the-border-and-gridline-styles-in-the-datagrid.md)中的框線和格線樣式。</span><span class="sxs-lookup"><span data-stu-id="3f976-137">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>

- <span data-ttu-id="3f976-138">啟用或限制控制項的<xref:System.Windows.Forms.DataGridView>使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="3f976-138">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3f976-139">如需詳細資訊，請參閱[如何：防止在 Windows Forms DataGridView 控制項](prevent-row-addition-and-deletion-datagridview.md)中新增和刪除資料列, 以及[如何:將 Windows Forms DataGridView 控制項](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)中的資料行設為唯讀。</span><span class="sxs-lookup"><span data-stu-id="3f976-139">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="3f976-140">驗證控制項的<xref:System.Windows.Forms.DataGridView>使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="3f976-140">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3f976-141">如需詳細資訊，請參閱[逐步解說：驗證 Windows Forms DataGridView 控制項](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)中的資料。</span><span class="sxs-lookup"><span data-stu-id="3f976-141">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="3f976-142">使用虛擬模式處理非常大型的資料集。</span><span class="sxs-lookup"><span data-stu-id="3f976-142">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="3f976-143">如需詳細資訊，請參閱[逐步解說：在 Windows Forms DataGridView 控制項](implementing-virtual-mode-wf-datagridview-control.md)中執行虛擬模式。</span><span class="sxs-lookup"><span data-stu-id="3f976-143">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>

- <span data-ttu-id="3f976-144">自訂儲存格的外觀。</span><span class="sxs-lookup"><span data-stu-id="3f976-144">Customize the appearance of cells.</span></span> <span data-ttu-id="3f976-145">如需詳細資訊，請參閱[如何：在 Windows Forms DataGridView 控制項](customize-the-appearance-of-cells-in-the-datagrid.md)中自訂儲存格的外觀, 以及[如何:設定 Windows Forms DataGridView 控制項](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)的預設儲存格樣式。</span><span class="sxs-lookup"><span data-stu-id="3f976-145">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3f976-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f976-146">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="3f976-147">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="3f976-147">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3f976-148">如何：使用兩個 Windows Forms DataGridView 控制項建立主要/詳細表單</span><span class="sxs-lookup"><span data-stu-id="3f976-148">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](create-a-master-detail-form-using-two-datagridviews.md)
- [<span data-ttu-id="3f976-149">保護連線資訊</span><span class="sxs-lookup"><span data-stu-id="3f976-149">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
