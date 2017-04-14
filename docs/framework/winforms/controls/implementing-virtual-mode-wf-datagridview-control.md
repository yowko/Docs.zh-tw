---
title: "逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "資料 [Windows Form], 管理大型資料集"
  - "DataGridView 控制項 [Windows Form], 大型資料集"
  - "DataGridView 控制項 [Windows Form], 虛擬模式"
  - "虛擬模式, 逐步解說"
  - "逐步解說 [Windows Form], DataGridView 控制項"
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式
當您要在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示相當大量的表格式資料時，您可以將 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性設定為 `true`，並明確管理控制項與其資料存放區的互動。  這讓您可以在這種情況下微調控制項的效能。  
  
 <xref:System.Windows.Forms.DataGridView> 控制項提供幾個事件，您可以處理這些事件以與自訂的資料存放區互動。  此逐步解說會引導您完成實作這些事件處理常式的過程。  本節中的程式碼範例會使用一個非常簡單的資料來源以進行說明。  在實際執行設定中，您通常只會將需要顯示的資料列載入到快取區 \(Cache\) 中，並處理 <xref:System.Windows.Forms.DataGridView> 事件以與快取區互動和更新快取區。  如需詳細資訊，請參閱[在 Windows Form DataGridView 控制項中以 Just\-In\-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 若要將此主題中的程式碼複製為一份清單，請參閱 [如何：在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)。  
  
## 建立表單  
  
#### 若要實作虛擬模式  
  
1.  建立衍生自 <xref:System.Windows.Forms.Form> 並包含 <xref:System.Windows.Forms.DataGridView> 控制項的類別。  
  
     下列程式碼包含一些基本的初始設定。  它會宣告一些在稍後步驟中會用到的變數、提供 `Main` 方法，並在類別建構函式中提供簡單的表單配置。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  為表單的 <xref:System.Windows.Forms.Form.Load> 事件實作處理常式，此事件會初始化 <xref:System.Windows.Forms.DataGridView> 控制項，並將範例值填入資料存放區。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  實作 <xref:System.Windows.Forms.DataGridView.CellValueNeeded> 事件的處理常式，此事件會從資料存放區或目前正在編輯的 `Customer` 物件，擷取要求的儲存格值。  
  
     每當 <xref:System.Windows.Forms.DataGridView> 控制項需要繪製儲存格時，就會發生這個事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  實作 <xref:System.Windows.Forms.DataGridView.CellValuePushed> 事件的處理常式，此事件會在 `Customer` \(代表已編輯的資料列\) 物件中儲存已編輯的儲存格值。  每當使用者認可儲存格值的變更時，就會發生這個事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  實作 <xref:System.Windows.Forms.DataGridView.NewRowNeeded> 事件的處理常式，此事件會建立新的 `Customer` 物件 \(代表新建立的資料列\)。  
  
     每當使用者輸入新資料錄的資料列時，就會發生這個事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  實作 <xref:System.Windows.Forms.DataGridView.RowValidated> 事件的處理常式，此事件會將新的或已修改的資料列儲存到資料存放區。  
  
     每當使用者變更目前的資料列時，就會發生這個事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  實作 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> 事件的處理常式，此事件會指示當使用者在編輯模式中按兩次 ESC 鍵，或是在編輯模式之外按一次 ESC 鍵時，發出資料列還原信號，是否會發生 <xref:System.Windows.Forms.DataGridView.CancelRowEdit> 事件。  
  
     依據預設，當目前資料列中的任何儲存格被修改而且還原時，<xref:System.Windows.Forms.DataGridView.CancelRowEdit> 就會發生，除非在 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> 事件處理常式中，<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=fullName> 屬性是設定為 `true`。  當認可範圍是在執行階段決定時，這個事件相當有用。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  實作 <xref:System.Windows.Forms.DataGridView.CancelRowEdit> 事件的處理常式，此事件會捨棄 `Customer` 物件 \(代表目前的資料列\) 的值。  
  
     當使用者在編輯模式中按兩次 ESC 鍵發出資料列還原信號，或是在編輯模式之外按一次 ESC 時，就會發生這個事件。  如果目前的資料列中沒有儲存格被修改，或是在 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> 事件處理常式中，<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=fullName> 屬性的值已設定為 `false`，就不會發生這個事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. 實作 <xref:System.Windows.Forms.DataGridView.UserDeletingRow> 事件的處理常式，此事件會從資料存放區刪除現有的 `Customer` 物件或捨棄未儲存的 `Customer` 物件 \(代表新建立的資料列\)。  
  
     每當使用者按一下資料列行首並按 DELETE 鍵時，就會發生這個事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. 實作簡單的 `Customers` 類別，以代表這個程式碼範例所使用的資料項目。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## 測試應用程式  
 您現在可以測試表單以確定它的行為表現如預期般。  
  
#### 若要測試表單  
  
-   編譯及執行應用程式。  
  
     您將看到一個填入三筆客戶資料錄的 <xref:System.Windows.Forms.DataGridView> 控制項。  您可以在資料列中修改多個儲存格的值，然後在編輯模式中按 ESC 鍵兩次及在編輯模式之外按 ESC 鍵一次，以將整個資料列還原成其原始值。  當您在控制項中修改、加入或刪除資料列時，也會修改、加入和刪除資料存放區中的 `Customer` 物件。  
  
## 後續步驟  
 這個應用程式提供您對事件的基本認識，您必須處理這些事件以便在 <xref:System.Windows.Forms.DataGridView> 控制項中實作虛擬模式。  您可以用一些方式來改進這個基本應用程式：  
  
-   實作快取來自外部資料庫資料的資料存放區。  此快取區必須依需要擷取和捨棄值，因此它只會包含顯示所需的內容，並耗用用戶端電腦上非常少量的記憶體。  
  
-   依照您的需求，微調資料存放區的效能。  例如，您可能會使用較大的快取區大小，並將資料庫查詢的數目減到最少，來彌補緩慢的網路連接，而不要限制用戶端電腦的記憶體。  
  
 如需從外部資料庫快取值的詳細資訊，請參閱 [如何：在 Windows Form DataGridView 控制項中以 Just\-In\-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>   
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>   
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>   
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>   
 <xref:System.Windows.Forms.DataGridView.RowValidated>   
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>   
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>   
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>   
 [Windows Form DataGridView 控制項中的效能微調](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)   
 [縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)   
 [在 Windows Form DataGridView 控制項中以 Just\-In\-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)   
 [如何：在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)