---
title: "逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式"
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
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b9a70aaf2643811354cc9d7f6b51ed0805ca916
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5e494-102">逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="5e494-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5e494-103">當您想要顯示非常大量的表格式資料中<xref:System.Windows.Forms.DataGridView>控制項，您可以設定<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性`true`和明確地管理其資料存放區的控制項的互動。</span><span class="sxs-lookup"><span data-stu-id="5e494-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="5e494-104">這可讓您微調控制項在此情況下的效能。</span><span class="sxs-lookup"><span data-stu-id="5e494-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="5e494-105"><xref:System.Windows.Forms.DataGridView>控制項提供數個事件，您可以處理與自訂資料存放區互動。</span><span class="sxs-lookup"><span data-stu-id="5e494-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="5e494-106">本逐步解說會引導您實作這些事件處理常式的程序。</span><span class="sxs-lookup"><span data-stu-id="5e494-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="5e494-107">本主題的程式碼範例會使用非常簡單的資料來源，適用於示範用途。</span><span class="sxs-lookup"><span data-stu-id="5e494-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="5e494-108">在生產環境的設定中，通常會載入到快取中，顯示和處理您需要的資料列<xref:System.Windows.Forms.DataGridView>互動，並更新快取事件。</span><span class="sxs-lookup"><span data-stu-id="5e494-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="5e494-109">如需詳細資訊，請參閱[以 Just-In-Time 資料載入 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="5e494-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="5e494-110">若要為單一列出本主題中複製的程式碼，請參閱[How to： 在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="5e494-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="5e494-111">建立表單</span><span class="sxs-lookup"><span data-stu-id="5e494-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="5e494-112">若要實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="5e494-112">To implement virtual mode</span></span>  
  
1.  <span data-ttu-id="5e494-113">建立衍生自類別<xref:System.Windows.Forms.Form>且包含<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="5e494-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="5e494-114">下列程式碼包含一些基本的初始設定。</span><span class="sxs-lookup"><span data-stu-id="5e494-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="5e494-115">它宣告將在稍後步驟中使用的一些變數，可提供`Main`方法，並提供簡單的表單配置類別建構函式中。</span><span class="sxs-lookup"><span data-stu-id="5e494-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  <span data-ttu-id="5e494-116">實作您的表單的處理常式<xref:System.Windows.Forms.Form.Load>初始化的事件<xref:System.Windows.Forms.DataGridView>控制，並於其中填入資料存放區的範例值。</span><span class="sxs-lookup"><span data-stu-id="5e494-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  <span data-ttu-id="5e494-117">實作的處理常式<xref:System.Windows.Forms.DataGridView.CellValueNeeded>從資料存放區擷取要求的資料格的值的事件或`Customer`目前正在編輯的物件。</span><span class="sxs-lookup"><span data-stu-id="5e494-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="5e494-118">此事件會發生<xref:System.Windows.Forms.DataGridView>控制項需要繪製儲存格。</span><span class="sxs-lookup"><span data-stu-id="5e494-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  <span data-ttu-id="5e494-119">實作的處理常式<xref:System.Windows.Forms.DataGridView.CellValuePushed>儲存編輯過的資料格的值中的事件`Customer`物件，代表已編輯的資料列。</span><span class="sxs-lookup"><span data-stu-id="5e494-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="5e494-120">每當使用者認可儲存格值的變更，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="5e494-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  <span data-ttu-id="5e494-121">實作的處理常式<xref:System.Windows.Forms.DataGridView.NewRowNeeded>建立新的事件`Customer`物件，代表新建立的資料列。</span><span class="sxs-lookup"><span data-stu-id="5e494-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="5e494-122">每當使用者輸入新記錄的資料列，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="5e494-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  <span data-ttu-id="5e494-123">實作的處理常式<xref:System.Windows.Forms.DataGridView.RowValidated>將新的或修改資料列儲存至資料存放區的事件。</span><span class="sxs-lookup"><span data-stu-id="5e494-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="5e494-124">每當使用者變更目前的資料列，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="5e494-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  <span data-ttu-id="5e494-125">實作的處理常式<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件，表示是否<xref:System.Windows.Forms.DataGridView.CancelRowEdit>使用者表示資料列還原儲存格處於編輯模式下兩次或一次編輯模式之外，請按下 esc 鍵時，就會發生事件。</span><span class="sxs-lookup"><span data-stu-id="5e494-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="5e494-126">根據預設，<xref:System.Windows.Forms.DataGridView.CancelRowEdit>除非已修改目前的資料列中的任何資料格時，會發生在資料列還原<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>屬性設定為`true`中<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5e494-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="5e494-127">此事件時，認可範圍在執行階段決定。</span><span class="sxs-lookup"><span data-stu-id="5e494-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  <span data-ttu-id="5e494-128">實作的處理常式<xref:System.Windows.Forms.DataGridView.CancelRowEdit>捨棄的值的事件`Customer`物件，代表目前的資料列。</span><span class="sxs-lookup"><span data-stu-id="5e494-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="5e494-129">當使用者表示資料列還原儲存格處於編輯模式下兩次或一次編輯模式之外，請按下 esc 鍵時，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="5e494-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="5e494-130">如果目前資料列中的任何儲存格已經過不修改，或不會發生此事件的值<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>屬性已設定為`false`中<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5e494-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="5e494-131">實作的處理常式<xref:System.Windows.Forms.DataGridView.UserDeletingRow>刪除現有的事件`Customer`物件從資料存放區或捨棄未儲存`Customer`物件，代表新建立的資料列。</span><span class="sxs-lookup"><span data-stu-id="5e494-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="5e494-132">每當使用者按一下資料列標頭，然後按 DELETE 鍵刪除資料列，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="5e494-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="5e494-133">實作簡單`Customers`類別來代表此程式碼範例所使用的資料項目。</span><span class="sxs-lookup"><span data-stu-id="5e494-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="5e494-134">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="5e494-134">Testing the Application</span></span>  
 <span data-ttu-id="5e494-135">您現在可以測試表單，以確定其如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="5e494-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="5e494-136">若要測試表單</span><span class="sxs-lookup"><span data-stu-id="5e494-136">To test the form</span></span>  
  
-   <span data-ttu-id="5e494-137">編譯並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5e494-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="5e494-138">您會看到<xref:System.Windows.Forms.DataGridView>控制項填入三個客戶記錄。</span><span class="sxs-lookup"><span data-stu-id="5e494-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="5e494-139">您可以修改資料列中的多個資料格的值，並按 esc 鍵兩次編輯模式，且一次不編輯模式，以還原成其原始值的整個資料列。</span><span class="sxs-lookup"><span data-stu-id="5e494-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="5e494-140">當您修改、 新增或刪除資料列，在控制項中，`Customer`修改、 加入或刪除資料存放區中的物件。</span><span class="sxs-lookup"><span data-stu-id="5e494-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5e494-141">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5e494-141">Next Steps</span></span>  
 <span data-ttu-id="5e494-142">此應用程式可讓您的實作中的虛擬模式時，您必須處理事件的基本了解<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="5e494-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5e494-143">您可以改善這個基本的應用程式，在數種方式：</span><span class="sxs-lookup"><span data-stu-id="5e494-143">You can improve this basic application in a number of ways:</span></span>  
  
-   <span data-ttu-id="5e494-144">實作快取來自外部資料庫的資料存放區。</span><span class="sxs-lookup"><span data-stu-id="5e494-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="5e494-145">應該擷取快取，並捨棄為必要值，使其只包含什麼是顯示耗用少量的記憶體用戶端電腦上所需的。</span><span class="sxs-lookup"><span data-stu-id="5e494-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
-   <span data-ttu-id="5e494-146">微調的效能資料存放區，根據您的需求。</span><span class="sxs-lookup"><span data-stu-id="5e494-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="5e494-147">例如，您可以藉由使用較大的快取大小以及資料庫查詢的數目降到最低彌補低速網路連線，而不是用戶端電腦的記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="5e494-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="5e494-148">如需快取的值從外部資料庫的詳細資訊，請參閱[How to： 以 Just-In-Time 資料載入 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="5e494-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e494-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="5e494-149">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>  
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>  
 <xref:System.Windows.Forms.DataGridView.RowValidated>  
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>  
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>  
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>  
 [<span data-ttu-id="5e494-150">Windows Forms DataGridView 控制項中的效能微調</span><span class="sxs-lookup"><span data-stu-id="5e494-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="5e494-151">縮放 Windows Forms DataGridView 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="5e494-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="5e494-152">在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="5e494-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 [<span data-ttu-id="5e494-153">操作說明：在 Windows Forms DataGridView 控制項中實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="5e494-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
