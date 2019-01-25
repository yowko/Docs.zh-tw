---
title: 逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式
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
ms.openlocfilehash: 4b03500878fe0aef337ceb0c7f8374c7563776e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518055"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="35553-102">逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="35553-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="35553-103">當您想要顯示非常大量的中的表格式資料的地方<xref:System.Windows.Forms.DataGridView>控制項，您可以設定<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性設`true`並明確地管理其資料存放區的控制項的互動。</span><span class="sxs-lookup"><span data-stu-id="35553-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="35553-104">這可讓您微調控制項在此情況下的效能。</span><span class="sxs-lookup"><span data-stu-id="35553-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="35553-105"><xref:System.Windows.Forms.DataGridView>控制項提供數個事件，您可以處理與自訂資料存放區互動。</span><span class="sxs-lookup"><span data-stu-id="35553-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="35553-106">本逐步解說會引導您實作這些事件處理常式的程序。</span><span class="sxs-lookup"><span data-stu-id="35553-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="35553-107">本主題的程式碼範例會使用非常簡單的資料來源，供說明之用。</span><span class="sxs-lookup"><span data-stu-id="35553-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="35553-108">在生產環境設定中，您通常將載入您要顯示成的快取，並處理的資料列<xref:System.Windows.Forms.DataGridView>事件與互動，並更新快取。</span><span class="sxs-lookup"><span data-stu-id="35553-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="35553-109">如需詳細資訊，請參閱[以 Just-In-Time 資料載入 Windows Forms DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="35553-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="35553-110">若要複製一份清單列出本主題中的程式碼，請參閱[How to:實作虛擬模式中的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="35553-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="35553-111">建立表單</span><span class="sxs-lookup"><span data-stu-id="35553-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="35553-112">若要實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="35553-112">To implement virtual mode</span></span>  
  
1.  <span data-ttu-id="35553-113">建立衍生自類別<xref:System.Windows.Forms.Form>且包含<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="35553-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="35553-114">下列程式碼包含一些基本的初始化。</span><span class="sxs-lookup"><span data-stu-id="35553-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="35553-115">它會宣告一些變數，用以在稍後步驟中，提供`Main`方法，並提供簡單的表單中的版面配置的類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="35553-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  <span data-ttu-id="35553-116">實作您的表單的處理常式<xref:System.Windows.Forms.Form.Load>初始化的事件<xref:System.Windows.Forms.DataGridView>控制，並於其中填入資料存放區的範例值。</span><span class="sxs-lookup"><span data-stu-id="35553-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  <span data-ttu-id="35553-117">實作的處理常式<xref:System.Windows.Forms.DataGridView.CellValueNeeded>從資料存放區擷取要求的資料格的值的事件或`Customer`中編輯目前的物件。</span><span class="sxs-lookup"><span data-stu-id="35553-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="35553-118">這個事件就會發生<xref:System.Windows.Forms.DataGridView>控制項需要繪製儲存格。</span><span class="sxs-lookup"><span data-stu-id="35553-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  <span data-ttu-id="35553-119">實作的處理常式<xref:System.Windows.Forms.DataGridView.CellValuePushed>儲存已編輯儲存格的值中的事件`Customer`物件，表示編輯的資料列。</span><span class="sxs-lookup"><span data-stu-id="35553-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="35553-120">每當使用者認可儲存格值的變更，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="35553-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  <span data-ttu-id="35553-121">實作的處理常式<xref:System.Windows.Forms.DataGridView.NewRowNeeded>建立新的事件`Customer`物件，代表新建立的資料列。</span><span class="sxs-lookup"><span data-stu-id="35553-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="35553-122">每當使用者輸入新資料錄的資料列，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="35553-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  <span data-ttu-id="35553-123">實作的處理常式<xref:System.Windows.Forms.DataGridView.RowValidated>將新的或修改過的資料列儲存至資料存放區的事件。</span><span class="sxs-lookup"><span data-stu-id="35553-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="35553-124">每當使用者變更目前的資料列，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="35553-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  <span data-ttu-id="35553-125">實作的處理常式<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件，表示是否<xref:System.Windows.Forms.DataGridView.CancelRowEdit>事件會發生於使用者按下 esc 鍵，在編輯模式中的兩次或一次編輯模式外表示資料列回復。</span><span class="sxs-lookup"><span data-stu-id="35553-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="35553-126">根據預設，<xref:System.Windows.Forms.DataGridView.CancelRowEdit>除非已修改目前的資料列中的任何資料格時，會發生在資料列回復<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>屬性設定為`true`在<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="35553-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="35553-127">當認可範圍在執行階段決定時，這個事件會很實用。</span><span class="sxs-lookup"><span data-stu-id="35553-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  <span data-ttu-id="35553-128">實作的處理常式<xref:System.Windows.Forms.DataGridView.CancelRowEdit>的值就會捨棄的事件`Customer`物件，表示目前資料列。</span><span class="sxs-lookup"><span data-stu-id="35553-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="35553-129">當使用者按下 esc 鍵，在編輯模式中的兩次或一次編輯模式外表示資料列回復時，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="35553-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="35553-130">如果目前的資料列中沒有儲存格已經過修改或者不會發生此事件的值<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>屬性已設定為`false`在<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="35553-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="35553-131">實作的處理常式<xref:System.Windows.Forms.DataGridView.UserDeletingRow>會刪除現有的事件`Customer`資料存放區的物件或捨棄未儲存`Customer`物件，代表新建立的資料列。</span><span class="sxs-lookup"><span data-stu-id="35553-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="35553-132">每當使用者按一下資料列標頭，然後按 DELETE 鍵刪除的資料列，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="35553-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="35553-133">實作簡單`Customers`類別來代表此程式碼範例所使用的資料項目。</span><span class="sxs-lookup"><span data-stu-id="35553-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="35553-134">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="35553-134">Testing the Application</span></span>  
 <span data-ttu-id="35553-135">您現在可以測試表單，以確定它如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="35553-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="35553-136">若要測試表單</span><span class="sxs-lookup"><span data-stu-id="35553-136">To test the form</span></span>  
  
-   <span data-ttu-id="35553-137">編譯並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="35553-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="35553-138">您會看到<xref:System.Windows.Forms.DataGridView>控制項填入三個客戶記錄。</span><span class="sxs-lookup"><span data-stu-id="35553-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="35553-139">您可以修改資料列中的多個儲存格的值，並在編輯模式中的兩倍，另一次編輯模式，以還原為其原始值的整個資料列之外，請按下 esc 鍵。</span><span class="sxs-lookup"><span data-stu-id="35553-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="35553-140">當您修改、 新增或刪除資料列，在控制項中，`Customer`修改、 新增或刪除資料存放區中的物件。</span><span class="sxs-lookup"><span data-stu-id="35553-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="35553-141">後續步驟</span><span class="sxs-lookup"><span data-stu-id="35553-141">Next Steps</span></span>  
 <span data-ttu-id="35553-142">此應用程式可讓您實作虛擬模式中的，您必須處理的事件的基本了解<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="35553-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="35553-143">您可以改善此基本的應用程式，在數種方式：</span><span class="sxs-lookup"><span data-stu-id="35553-143">You can improve this basic application in a number of ways:</span></span>  
  
-   <span data-ttu-id="35553-144">實作外部的資料庫中的值會快取的資料存放區。</span><span class="sxs-lookup"><span data-stu-id="35553-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="35553-145">快取應擷取並捨棄視需要的值，使其只包含所需取用少量的記憶體用戶端電腦上時顯示。</span><span class="sxs-lookup"><span data-stu-id="35553-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
-   <span data-ttu-id="35553-146">微調效能的資料存放區，根據您的需求。</span><span class="sxs-lookup"><span data-stu-id="35553-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="35553-147">例如，您可以藉由使用較大的快取大小和減少資料庫的查詢數目補償低速網路連線，而不是用戶端電腦的記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="35553-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="35553-148">如需有關快取從外部資料庫的值的詳細資訊，請參閱[How to:實作虛擬模式，以在 Just-in-time 資料載入，在 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="35553-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35553-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35553-149">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [<span data-ttu-id="35553-150">Windows Forms DataGridView 控制項中的效能微調</span><span class="sxs-lookup"><span data-stu-id="35553-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="35553-151">縮放 Windows Forms DataGridView 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="35553-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="35553-152">在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="35553-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="35553-153">如何：在 Windows Form DataGridView 控制項中實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="35553-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
