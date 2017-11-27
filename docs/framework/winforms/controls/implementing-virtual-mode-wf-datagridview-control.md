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
ms.openlocfilehash: 31806d3ed13776e26634914b48bc887297ea4dab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式
當您想要顯示非常大量的表格式資料中<xref:System.Windows.Forms.DataGridView>控制項，您可以設定<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性`true`和明確地管理其資料存放區的控制項的互動。 這可讓您微調控制項在此情況下的效能。  
  
 <xref:System.Windows.Forms.DataGridView>控制項提供數個事件，您可以處理與自訂資料存放區互動。 本逐步解說會引導您實作這些事件處理常式的程序。 本主題的程式碼範例會使用非常簡單的資料來源，適用於示範用途。 在生產環境的設定中，通常會載入到快取中，顯示和處理您需要的資料列<xref:System.Windows.Forms.DataGridView>互動，並更新快取事件。 如需詳細資訊，請參閱[以 Just-In-Time 資料載入 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 若要為單一列出本主題中複製的程式碼，請參閱[How to： 在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="creating-the-form"></a>建立表單  
  
#### <a name="to-implement-virtual-mode"></a>若要實作虛擬模式  
  
1.  建立衍生自類別<xref:System.Windows.Forms.Form>且包含<xref:System.Windows.Forms.DataGridView>控制項。  
  
     下列程式碼包含一些基本的初始設定。 它宣告將在稍後步驟中使用的一些變數，可提供`Main`方法，並提供簡單的表單配置類別建構函式中。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  實作您的表單的處理常式<xref:System.Windows.Forms.Form.Load>初始化的事件<xref:System.Windows.Forms.DataGridView>控制，並於其中填入資料存放區的範例值。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  實作的處理常式<xref:System.Windows.Forms.DataGridView.CellValueNeeded>從資料存放區擷取要求的資料格的值的事件或`Customer`目前正在編輯的物件。  
  
     此事件會發生<xref:System.Windows.Forms.DataGridView>控制項需要繪製儲存格。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  實作的處理常式<xref:System.Windows.Forms.DataGridView.CellValuePushed>儲存編輯過的資料格的值中的事件`Customer`物件，代表已編輯的資料列。 每當使用者認可儲存格值的變更，就會發生此事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  實作的處理常式<xref:System.Windows.Forms.DataGridView.NewRowNeeded>建立新的事件`Customer`物件，代表新建立的資料列。  
  
     每當使用者輸入新記錄的資料列，就會發生此事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  實作的處理常式<xref:System.Windows.Forms.DataGridView.RowValidated>將新的或修改資料列儲存至資料存放區的事件。  
  
     每當使用者變更目前的資料列，就會發生此事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  實作的處理常式<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件，表示是否<xref:System.Windows.Forms.DataGridView.CancelRowEdit>使用者表示資料列還原儲存格處於編輯模式下兩次或一次編輯模式之外，請按下 esc 鍵時，就會發生事件。  
  
     根據預設，<xref:System.Windows.Forms.DataGridView.CancelRowEdit>除非已修改目前的資料列中的任何資料格時，會發生在資料列還原<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>屬性設定為`true`中<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件處理常式。 此事件時，認可範圍在執行階段決定。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  實作的處理常式<xref:System.Windows.Forms.DataGridView.CancelRowEdit>捨棄的值的事件`Customer`物件，代表目前的資料列。  
  
     當使用者表示資料列還原儲存格處於編輯模式下兩次或一次編輯模式之外，請按下 esc 鍵時，就會發生此事件。 如果目前資料列中的任何儲存格已經過不修改，或不會發生此事件的值<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>屬性已設定為`false`中<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件處理常式。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. 實作的處理常式<xref:System.Windows.Forms.DataGridView.UserDeletingRow>刪除現有的事件`Customer`物件從資料存放區或捨棄未儲存`Customer`物件，代表新建立的資料列。  
  
     每當使用者按一下資料列標頭，然後按 DELETE 鍵刪除資料列，就會發生此事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. 實作簡單`Customers`類別來代表此程式碼範例所使用的資料項目。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 您現在可以測試表單，以確定其如預期般運作。  
  
#### <a name="to-test-the-form"></a>若要測試表單  
  
-   編譯並執行應用程式。  
  
     您會看到<xref:System.Windows.Forms.DataGridView>控制項填入三個客戶記錄。 您可以修改資料列中的多個資料格的值，並按 esc 鍵兩次編輯模式，且一次不編輯模式，以還原成其原始值的整個資料列。 當您修改、 新增或刪除資料列，在控制項中，`Customer`修改、 加入或刪除資料存放區中的物件。  
  
## <a name="next-steps"></a>後續步驟  
 此應用程式可讓您的實作中的虛擬模式時，您必須處理事件的基本了解<xref:System.Windows.Forms.DataGridView>控制項。 您可以改善這個基本的應用程式，在數種方式：  
  
-   實作快取來自外部資料庫的資料存放區。 應該擷取快取，並捨棄為必要值，使其只包含什麼是顯示耗用少量的記憶體用戶端電腦上所需的。  
  
-   微調的效能資料存放區，根據您的需求。 例如，您可以藉由使用較大的快取大小以及資料庫查詢的數目降到最低彌補低速網路連線，而不是用戶端電腦的記憶體限制。  
  
 如需快取的值從外部資料庫的詳細資訊，請參閱[How to： 以 Just-In-Time 資料載入 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>  
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>  
 <xref:System.Windows.Forms.DataGridView.RowValidated>  
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>  
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>  
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>  
 [Windows Forms DataGridView 控制項中的效能微調](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [縮放 Windows Forms DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 [操作說明：在 Windows Forms DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
