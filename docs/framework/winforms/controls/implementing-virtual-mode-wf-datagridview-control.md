---
title: 逐步解說：在 Windows Forms DataGridView 控制項中實作虛擬模式
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
ms.openlocfilehash: 7f6bf1703a6536f4d22b3a2fbe412579c59d39dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973767"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>逐步解說：在 Windows Forms DataGridView 控制項中實作虛擬模式
當您想要顯示非常大量的中的表格式資料的地方<xref:System.Windows.Forms.DataGridView>控制項，您可以設定<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性設`true`並明確地管理其資料存放區的控制項的互動。 這可讓您微調控制項在此情況下的效能。  
  
 <xref:System.Windows.Forms.DataGridView>控制項提供數個事件，您可以處理與自訂資料存放區互動。 本逐步解說會引導您實作這些事件處理常式的程序。 本主題的程式碼範例會使用非常簡單的資料來源，供說明之用。 在生產環境設定中，您通常將載入您要顯示成的快取，並處理的資料列<xref:System.Windows.Forms.DataGridView>事件與互動，並更新快取。 如需詳細資訊，請參閱[以 Just-In-Time 資料載入 Windows Forms DataGridView 控制項中實作虛擬模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 若要將此主題中的程式碼複製為單一清單，請參閱[如何：實作虛擬模式中的 Windows Form DataGridView 控制項](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="creating-the-form"></a>建立表單  
  
#### <a name="to-implement-virtual-mode"></a>若要實作虛擬模式  
  
1. 建立衍生自類別<xref:System.Windows.Forms.Form>且包含<xref:System.Windows.Forms.DataGridView>控制項。  
  
     下列程式碼包含一些基本的初始化。 它會宣告一些變數，用以在稍後步驟中，提供`Main`方法，並提供簡單的表單中的版面配置的類別建構函式。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. 實作您的表單的處理常式<xref:System.Windows.Forms.Form.Load>初始化的事件<xref:System.Windows.Forms.DataGridView>控制，並於其中填入資料存放區的範例值。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. 實作的處理常式<xref:System.Windows.Forms.DataGridView.CellValueNeeded>從資料存放區擷取要求的資料格的值的事件或`Customer`中編輯目前的物件。  
  
     這個事件就會發生<xref:System.Windows.Forms.DataGridView>控制項需要繪製儲存格。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. 實作的處理常式<xref:System.Windows.Forms.DataGridView.CellValuePushed>儲存已編輯儲存格的值中的事件`Customer`物件，表示編輯的資料列。 每當使用者認可儲存格值的變更，就會發生此事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. 實作的處理常式<xref:System.Windows.Forms.DataGridView.NewRowNeeded>建立新的事件`Customer`物件，代表新建立的資料列。  
  
     每當使用者輸入新資料錄的資料列，就會發生此事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. 實作的處理常式<xref:System.Windows.Forms.DataGridView.RowValidated>將新的或修改過的資料列儲存至資料存放區的事件。  
  
     每當使用者變更目前的資料列，就會發生此事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. 實作的處理常式<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件，表示是否<xref:System.Windows.Forms.DataGridView.CancelRowEdit>事件會發生於使用者按下 esc 鍵，在編輯模式中的兩次或一次編輯模式外表示資料列回復。  
  
     根據預設，<xref:System.Windows.Forms.DataGridView.CancelRowEdit>除非已修改目前的資料列中的任何資料格時，會發生在資料列回復<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>屬性設定為`true`在<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件處理常式。 當認可範圍在執行階段決定時，這個事件會很實用。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. 實作的處理常式<xref:System.Windows.Forms.DataGridView.CancelRowEdit>的值就會捨棄的事件`Customer`物件，表示目前資料列。  
  
     當使用者按下 esc 鍵，在編輯模式中的兩次或一次編輯模式外表示資料列回復時，就會發生此事件。 如果目前的資料列中沒有儲存格已經過修改或者不會發生此事件的值<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>屬性已設定為`false`在<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件處理常式。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. 實作的處理常式<xref:System.Windows.Forms.DataGridView.UserDeletingRow>會刪除現有的事件`Customer`資料存放區的物件或捨棄未儲存`Customer`物件，代表新建立的資料列。  
  
     每當使用者按一下資料列標頭，然後按 DELETE 鍵刪除的資料列，就會發生此事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. 實作簡單`Customers`類別來代表此程式碼範例所使用的資料項目。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 您現在可以測試表單，以確定它如預期般運作。  
  
#### <a name="to-test-the-form"></a>若要測試表單  
  
- 編譯並執行應用程式。  
  
     您會看到<xref:System.Windows.Forms.DataGridView>控制項填入三個客戶記錄。 您可以修改資料列中的多個儲存格的值，並在編輯模式中的兩倍，另一次編輯模式，以還原為其原始值的整個資料列之外，請按下 esc 鍵。 當您修改、 新增或刪除資料列，在控制項中，`Customer`修改、 新增或刪除資料存放區中的物件。  
  
## <a name="next-steps"></a>後續步驟  
 此應用程式可讓您實作虛擬模式中的，您必須處理的事件的基本了解<xref:System.Windows.Forms.DataGridView>控制項。 您可以改善此基本的應用程式，在數種方式：  
  
- 實作外部的資料庫中的值會快取的資料存放區。 快取應擷取並捨棄視需要的值，使其只包含所需取用少量的記憶體用戶端電腦上時顯示。  
  
- 微調效能的資料存放區，根據您的需求。 例如，您可以藉由使用較大的快取大小和減少資料庫的查詢數目補償低速網路連線，而不是用戶端電腦的記憶體限制。  
  
 如需有關快取從外部資料庫的值的詳細資訊，請參閱[How to:實作虛擬模式，以在 Just-in-time 資料載入，在 Windows Form DataGridView 控制項](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)。  
  
## <a name="see-also"></a>另請參閱

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
- [如何：在 Windows Form DataGridView 控制項中實作虛擬模式](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
