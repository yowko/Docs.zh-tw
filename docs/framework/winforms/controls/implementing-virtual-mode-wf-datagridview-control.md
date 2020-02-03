---
title: 逐步解說：在 DataGridView 控制項中執行虛擬模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
ms.openlocfilehash: 5db97b321238bc371c94e627a387bd83ca31b58a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746524"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="4e474-102">逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="4e474-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4e474-103">當您想要在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示非常大量的表格式資料時，您可以將 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性設定為 `true` 並明確管理控制項與其資料存放區的互動。</span><span class="sxs-lookup"><span data-stu-id="4e474-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="4e474-104">這可讓您在這種情況下微調控制項的效能。</span><span class="sxs-lookup"><span data-stu-id="4e474-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="4e474-105"><xref:System.Windows.Forms.DataGridView> 控制項提供數個事件，可讓您處理以與自訂資料存放區互動。</span><span class="sxs-lookup"><span data-stu-id="4e474-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="4e474-106">本逐步解說會引導您完成這些事件處理常式的處理。</span><span class="sxs-lookup"><span data-stu-id="4e474-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="4e474-107">本主題中的程式碼範例會使用非常簡單的資料來源做為說明之用。</span><span class="sxs-lookup"><span data-stu-id="4e474-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="4e474-108">在生產環境設定中，您通常只會載入需要顯示在快取中的資料列，並處理 <xref:System.Windows.Forms.DataGridView> 事件來與快取互動並加以更新。</span><span class="sxs-lookup"><span data-stu-id="4e474-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="4e474-109">如需詳細資訊，請參閱[在 Windows Forms DataGridView 控制項中使用即時資料載入來執行虛擬模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="4e474-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="4e474-110">若要將本主題中的程式碼複製成單一清單，請參閱 how [to：在 Windows Forms DataGridView 控制項中執行虛擬模式](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="4e474-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="4e474-111">建立表單</span><span class="sxs-lookup"><span data-stu-id="4e474-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="4e474-112">若要執行虛擬模式</span><span class="sxs-lookup"><span data-stu-id="4e474-112">To implement virtual mode</span></span>  
  
1. <span data-ttu-id="4e474-113">建立衍生自 <xref:System.Windows.Forms.Form> 並包含 <xref:System.Windows.Forms.DataGridView> 控制項的類別。</span><span class="sxs-lookup"><span data-stu-id="4e474-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="4e474-114">下列程式碼包含一些基本的初始化。</span><span class="sxs-lookup"><span data-stu-id="4e474-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="4e474-115">它會宣告一些將在後續步驟中使用的變數、提供 `Main` 方法，並在類別的函式中提供簡單的表單版面配置。</span><span class="sxs-lookup"><span data-stu-id="4e474-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. <span data-ttu-id="4e474-116">為表單的 <xref:System.Windows.Forms.Form.Load> 事件執行處理常式，以初始化 <xref:System.Windows.Forms.DataGridView> 控制項，並使用範例值填入資料存放區。</span><span class="sxs-lookup"><span data-stu-id="4e474-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. <span data-ttu-id="4e474-117">執行 <xref:System.Windows.Forms.DataGridView.CellValueNeeded> 事件的處理常式，以從資料存放區或目前在編輯中的 `Customer` 物件，抓取要求的儲存格值。</span><span class="sxs-lookup"><span data-stu-id="4e474-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="4e474-118">每當 <xref:System.Windows.Forms.DataGridView> 控制項需要繪製儲存格時，就會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="4e474-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. <span data-ttu-id="4e474-119">執行 <xref:System.Windows.Forms.DataGridView.CellValuePushed> 事件的處理常式，這個事件會將已編輯的資料格值儲存在代表已編輯資料列的 `Customer` 物件中。</span><span class="sxs-lookup"><span data-stu-id="4e474-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="4e474-120">每當使用者認可資料格值變更時，就會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="4e474-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. <span data-ttu-id="4e474-121">執行 <xref:System.Windows.Forms.DataGridView.NewRowNeeded> 事件的處理常式，以建立代表新建立之資料列的新 `Customer` 物件。</span><span class="sxs-lookup"><span data-stu-id="4e474-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="4e474-122">每當使用者輸入新記錄的資料列時，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="4e474-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. <span data-ttu-id="4e474-123">為 <xref:System.Windows.Forms.DataGridView.RowValidated> 事件執行處理常式，以將新的或修改過的資料列儲存至資料存放區。</span><span class="sxs-lookup"><span data-stu-id="4e474-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="4e474-124">每當使用者變更目前的資料列時，就會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="4e474-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. <span data-ttu-id="4e474-125">執行 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> 事件的處理常式，指出當使用者在編輯模式中按下 ESC 鍵或在編輯模式之外按兩次時，是否會發出 <xref:System.Windows.Forms.DataGridView.CancelRowEdit> 事件。</span><span class="sxs-lookup"><span data-stu-id="4e474-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="4e474-126">根據預設，除非已修改目前資料列中的任何資料格，否則 <xref:System.Windows.Forms.DataGridView.CancelRowEdit> 會發生在資料列回復上，除非 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> 事件處理常式中的 <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="4e474-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="4e474-127">當認可範圍是在執行時間決定時，這個事件會很有用。</span><span class="sxs-lookup"><span data-stu-id="4e474-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. <span data-ttu-id="4e474-128">執行 <xref:System.Windows.Forms.DataGridView.CancelRowEdit> 事件的處理常式，其會捨棄代表目前資料列之 `Customer` 物件的值。</span><span class="sxs-lookup"><span data-stu-id="4e474-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="4e474-129">當使用者在編輯模式中按下 ESC 鍵，或在編輯模式之外按兩次時，就會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="4e474-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="4e474-130">如果目前資料列中沒有任何資料格已修改，或 <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> 屬性的值已設定為 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> 事件處理常式中 `false`，就不會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="4e474-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="4e474-131">執行 <xref:System.Windows.Forms.DataGridView.UserDeletingRow> 事件的處理常式，以從資料存放區中刪除現有的 `Customer` 物件，或捨棄代表新建立之資料列的未儲存 `Customer` 物件。</span><span class="sxs-lookup"><span data-stu-id="4e474-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="4e474-132">每當使用者藉由按一下資料列標題並按下 DELETE 鍵來刪除資料列時，就會發生這個事件。</span><span class="sxs-lookup"><span data-stu-id="4e474-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="4e474-133">執行簡單的 `Customers` 類別，以代表此程式碼範例所使用的資料項目。</span><span class="sxs-lookup"><span data-stu-id="4e474-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="4e474-134">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="4e474-134">Testing the Application</span></span>  
 <span data-ttu-id="4e474-135">您現在可以測試表單，以確定它會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="4e474-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="4e474-136">測試表單</span><span class="sxs-lookup"><span data-stu-id="4e474-136">To test the form</span></span>  
  
- <span data-ttu-id="4e474-137">編譯並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e474-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="4e474-138">您會看到填入三個客戶記錄的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="4e474-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="4e474-139">您可以修改資料列中的多個儲存格的值，然後在編輯模式和編輯模式之外按兩次 ESC 鍵，將整個資料列還原成其原始值。</span><span class="sxs-lookup"><span data-stu-id="4e474-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="4e474-140">當您修改、加入或刪除控制項中的資料列時，也會修改、加入或刪除資料存放區中的 `Customer` 物件。</span><span class="sxs-lookup"><span data-stu-id="4e474-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4e474-141">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4e474-141">Next Steps</span></span>  
 <span data-ttu-id="4e474-142">此應用程式可讓您對在 <xref:System.Windows.Forms.DataGridView> 控制項中執行虛擬模式所必須處理的事件有基本瞭解。</span><span class="sxs-lookup"><span data-stu-id="4e474-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="4e474-143">您可以透過數種方式來改善此基本應用程式：</span><span class="sxs-lookup"><span data-stu-id="4e474-143">You can improve this basic application in a number of ways:</span></span>  
  
- <span data-ttu-id="4e474-144">執行可從外部資料庫快取值的資料存放區。</span><span class="sxs-lookup"><span data-stu-id="4e474-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="4e474-145">快取應視需要抓取並捨棄值，使其只包含在用戶端電腦上耗用少量記憶體時所需的顯示內容。</span><span class="sxs-lookup"><span data-stu-id="4e474-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
- <span data-ttu-id="4e474-146">根據您的需求微調資料存放區的效能。</span><span class="sxs-lookup"><span data-stu-id="4e474-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="4e474-147">例如，您可能會想要使用較大的快取大小來補償緩慢的網路連線，而不是用戶端電腦記憶體的限制，並將資料庫查詢的數目減至最少。</span><span class="sxs-lookup"><span data-stu-id="4e474-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="4e474-148">如需從外部資料庫快取值的詳細資訊，請參閱 how [to：在 Windows Forms DataGridView 控制項中使用即時資料載入來執行虛擬模式](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="4e474-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e474-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e474-149">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [<span data-ttu-id="4e474-150">Windows Forms DataGridView 控制項中的效能微調</span><span class="sxs-lookup"><span data-stu-id="4e474-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="4e474-151">縮放 Windows Forms DataGridView 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="4e474-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="4e474-152">在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="4e474-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="4e474-153">操作說明：在 Windows Forms DataGridView 控制項中實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="4e474-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
