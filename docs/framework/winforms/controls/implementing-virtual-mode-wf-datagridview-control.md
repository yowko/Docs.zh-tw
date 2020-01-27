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
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式
當您想要在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示非常大量的表格式資料時，您可以將 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性設定為 `true` 並明確管理控制項與其資料存放區的互動。 這可讓您在這種情況下微調控制項的效能。  
  
 <xref:System.Windows.Forms.DataGridView> 控制項提供數個事件，可讓您處理以與自訂資料存放區互動。 本逐步解說會引導您完成這些事件處理常式的處理。 本主題中的程式碼範例會使用非常簡單的資料來源做為說明之用。 在生產環境設定中，您通常只會載入需要顯示在快取中的資料列，並處理 <xref:System.Windows.Forms.DataGridView> 事件來與快取互動並加以更新。 如需詳細資訊，請參閱[在 Windows Forms DataGridView 控制項中使用即時資料載入來執行虛擬模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 若要將本主題中的程式碼複製成單一清單，請參閱 how [to：在 Windows Forms DataGridView 控制項中執行虛擬模式](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="creating-the-form"></a>建立表單  
  
#### <a name="to-implement-virtual-mode"></a>若要執行虛擬模式  
  
1. 建立衍生自 <xref:System.Windows.Forms.Form> 並包含 <xref:System.Windows.Forms.DataGridView> 控制項的類別。  
  
     下列程式碼包含一些基本的初始化。 它會宣告一些將在後續步驟中使用的變數、提供 `Main` 方法，並在類別的函式中提供簡單的表單版面配置。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. 為表單的 <xref:System.Windows.Forms.Form.Load> 事件執行處理常式，以初始化 <xref:System.Windows.Forms.DataGridView> 控制項，並使用範例值填入資料存放區。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. 執行 <xref:System.Windows.Forms.DataGridView.CellValueNeeded> 事件的處理常式，以從資料存放區或目前在編輯中的 `Customer` 物件，抓取要求的儲存格值。  
  
     每當 <xref:System.Windows.Forms.DataGridView> 控制項需要繪製儲存格時，就會發生這個事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. 執行 <xref:System.Windows.Forms.DataGridView.CellValuePushed> 事件的處理常式，這個事件會將已編輯的資料格值儲存在代表已編輯資料列的 `Customer` 物件中。 每當使用者認可資料格值變更時，就會發生這個事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. 執行 <xref:System.Windows.Forms.DataGridView.NewRowNeeded> 事件的處理常式，以建立代表新建立之資料列的新 `Customer` 物件。  
  
     每當使用者輸入新記錄的資料列時，就會發生此事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. 為 <xref:System.Windows.Forms.DataGridView.RowValidated> 事件執行處理常式，以將新的或修改過的資料列儲存至資料存放區。  
  
     每當使用者變更目前的資料列時，就會發生這個事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. 執行 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> 事件的處理常式，指出當使用者在編輯模式中按下 ESC 鍵或在編輯模式之外按兩次時，是否會發出 <xref:System.Windows.Forms.DataGridView.CancelRowEdit> 事件。  
  
     根據預設，除非已修改目前資料列中的任何資料格，否則 <xref:System.Windows.Forms.DataGridView.CancelRowEdit> 會發生在資料列回復上，除非 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> 事件處理常式中的 <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> 屬性設定為 `true`。 當認可範圍是在執行時間決定時，這個事件會很有用。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. 執行 <xref:System.Windows.Forms.DataGridView.CancelRowEdit> 事件的處理常式，其會捨棄代表目前資料列之 `Customer` 物件的值。  
  
     當使用者在編輯模式中按下 ESC 鍵，或在編輯模式之外按兩次時，就會發生這個事件。 如果目前資料列中沒有任何資料格已修改，或 <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> 屬性的值已設定為 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> 事件處理常式中 `false`，就不會發生這個事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. 執行 <xref:System.Windows.Forms.DataGridView.UserDeletingRow> 事件的處理常式，以從資料存放區中刪除現有的 `Customer` 物件，或捨棄代表新建立之資料列的未儲存 `Customer` 物件。  
  
     每當使用者藉由按一下資料列標題並按下 DELETE 鍵來刪除資料列時，就會發生這個事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. 執行簡單的 `Customers` 類別，以代表此程式碼範例所使用的資料項目。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 您現在可以測試表單，以確定它會如預期般運作。  
  
#### <a name="to-test-the-form"></a>測試表單  
  
- 編譯並執行應用程式。  
  
     您會看到填入三個客戶記錄的 <xref:System.Windows.Forms.DataGridView> 控制項。 您可以修改資料列中的多個儲存格的值，然後在編輯模式和編輯模式之外按兩次 ESC 鍵，將整個資料列還原成其原始值。 當您修改、加入或刪除控制項中的資料列時，也會修改、加入或刪除資料存放區中的 `Customer` 物件。  
  
## <a name="next-steps"></a>後續步驟  
 此應用程式可讓您對在 <xref:System.Windows.Forms.DataGridView> 控制項中執行虛擬模式所必須處理的事件有基本瞭解。 您可以透過數種方式來改善此基本應用程式：  
  
- 執行可從外部資料庫快取值的資料存放區。 快取應視需要抓取並捨棄值，使其只包含在用戶端電腦上耗用少量記憶體時所需的顯示內容。  
  
- 根據您的需求微調資料存放區的效能。 例如，您可能會想要使用較大的快取大小來補償緩慢的網路連線，而不是用戶端電腦記憶體的限制，並將資料庫查詢的數目減至最少。  
  
 如需從外部資料庫快取值的詳細資訊，請參閱 how [to：在 Windows Forms DataGridView 控制項中使用即時資料載入來執行虛擬模式](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [Windows Forms DataGridView 控制項中的效能微調](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [縮放 Windows Forms DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [操作說明：在 Windows Forms DataGridView 控制項中實作虛擬模式](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
