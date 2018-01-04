---
title: "逐步解說：在 WPF 中裝載 Win32 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0795875b4d5f1a91b7c570320acb078b845ae712
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>逐步解說：在 WPF 中裝載 Win32 控制項
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。 不過，當您擁有了大筆投資的[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]程式碼，它可能是更有效率地重複使用最少部分中的程式碼程式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]而不是它完全重寫應用程式。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供簡單的機制，以裝載[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗，請在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。  
  
 本主題會引導您透過應用程式，[裝載 WPF 範例中的 Win32 ListBox 控制項](http://go.microsoft.com/fwlink/?LinkID=159998)、 該主機[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]清單方塊控制項。 可以擴充這個一般程序，以裝載任何[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗。  
  
  
<a name="requirements"></a>   
## <a name="requirements"></a>需求  
 本主題假設與這兩個基本的認識[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]程式設計。 如需基本簡介[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程式設計，請參閱[入門](../../../../docs/framework/wpf/getting-started/index.md)。 如需簡介[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]程式設計，您應該參考任何許多書籍主旨，特別是*程式設計 Windows* Charles Petzold 所。  
  
 因為隨附本主題的範例中實作[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]，它會使用[!INCLUDE[TLA#tla_pinvoke](../../../../includes/tlasharptla-pinvoke-md.md)]存取[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]。 疐裾[!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)]會有所助益，但不是重要。  
  
> [!NOTE]
>  本主題包含一些來自相關聯範例的程式碼範例。 不過，為了方便閱讀，並未包含完整的範例程式碼。 您可以取得，或檢視完整的程式碼[裝載 WPF 範例中的 Win32 ListBox 控制項](http://go.microsoft.com/fwlink/?LinkID=159998)。  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>基本程序  
 本節將概述裝載的基本程序[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗上的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。 其餘各節將說明每個步驟的詳細資料。  
  
 基本裝載程序如下︰  
  
1.  實作[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面，即可主控視窗。 若要建立的其中一個技術是<xref:System.Windows.Controls.Border>保留裝載視窗的頁面區段的項目。  
  
2.  實作類別來裝載控制項是繼承自<xref:System.Windows.Interop.HwndHost>。  
  
3.  在該類別，覆寫<xref:System.Windows.Interop.HwndHost>類別成員<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>。  
  
4.  建立裝載之的視窗的視窗，其中包含子系[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。 雖然傳統[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程式設計不需要明確地將使用它，裝載的網頁是一種視窗控制代碼 (HWND)。 接收頁面 HWND 透過`hwndParent`參數<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>方法。 裝載的視窗應該建立為此 HWND 的子系。  
  
5.  建立主視窗之後，即會傳回裝載之視窗的 HWND。 如果您想要主控一或多個[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]控制項，您通常建立主機視窗為 HWND 的子系，並讓控制項視窗的子系該主機。 包裝控制項在主視窗中提供簡單的方式，讓您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面上要從控制項，接收通知的處理某些特定[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]問題 HWND 界限之間的通知。  
  
6.  處理傳送至主視窗的已選取訊息，例如來自子控制項的通知。 執行這項作業的方法有兩種。  
  
    -   如果您想要處理訊息中裝載的類別，覆寫<xref:System.Windows.Interop.HwndHost.WndProc%2A>方法<xref:System.Windows.Interop.HwndHost>類別。  
  
    -   如果您想要有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]處理訊息、 處理<xref:System.Windows.Interop.HwndHost>類別<xref:System.Windows.Interop.HwndHost.MessageHook>中您的程式碼後置事件。 針對裝載的視窗接收到的每個訊息，都會發生此事件。 如果您選擇此選項時，您必須仍覆寫<xref:System.Windows.Interop.HwndHost.WndProc%2A>，但是您只需要最簡單的實作。  
  
7.  覆寫<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>和<xref:System.Windows.Interop.HwndHost.WndProc%2A>方法<xref:System.Windows.Interop.HwndHost>。 您必須覆寫這些方法來滿足<xref:System.Windows.Interop.HwndHost>合約，但是您可能只需要提供最簡單的實作。  
  
8.  在程式碼後置檔案中，建立控制項的裝載類別的執行個體，並讓它的子系<xref:System.Windows.Controls.Border>要裝載在視窗的項目。  
  
9. 與之通訊所裝載之視窗傳送[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]訊息和來自其子視窗，例如控制項傳送的告知的處理訊息。  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>實作版面配置  
 針對版面配置[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]裝載 ListBox 控制項的頁面包含兩個區域。 頁面的左半部裝載數個[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項，可提供[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]，可讓您操作[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]控制項。 頁面的右上角具有 ListBox 託管控制項的方形區域。  
  
 實作這個配置的程式碼是相當簡單。 根項目是<xref:System.Windows.Controls.DockPanel>，有兩個子項目。 第一個是<xref:System.Windows.Controls.Border>裝載 ListBox 控制項項目。 它會佔用頁面右上角的 200x200 方形。 第二個是<xref:System.Windows.Controls.StackPanel>包含一系列的項目[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]顯示資訊，並讓您藉由設定操作 ListBox 控制項的控制項公開互通性的屬性。 針對每個元素的子系<xref:System.Windows.Controls.StackPanel>，請參閱 < 參考資料，如需詳細資訊，這些項目為何，或它們的用途上使用的各種項目，這些會列在下列範例程式碼，但不是會這裡所說明 (basic互通性的模型不需要它們，只要是將某些互動功能加入至範例）。  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>實作類別以裝載 Microsoft Win32 控制項  
 此範例的核心是實際裝載 ControlHost.cs 控制項的類別。 它繼承自<xref:System.Windows.Interop.HwndHost>。 建構函式接受兩個參數、 高度和寬度、 高度和寬度對應<xref:System.Windows.Controls.Border>裝載 ListBox 控制項項目。 這些值將稍後用來確保控制相符項目的大小<xref:System.Windows.Controls.Border>項目。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 還有一組常數。 這些常數主要是取自 Winuser.h，並可讓您使用傳統的名稱呼叫時[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函式。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>覆寫 BuildWindowCore 以建立 Microsoft Win32 視窗  
 您覆寫此方法以建立[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗，將此網頁所裝載，並讓視窗和頁面之間的連線。 因為此範例包含裝載 ListBox 控制項，所以會建立兩個視窗。 第一個是實際上由主控視窗[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。 ListBox 控制項會建立為該視窗的子系。  
  
 此方法的原因是要簡化接收來自控制項之通知的程序。 <xref:System.Windows.Interop.HwndHost>類別可讓您處理訊息傳送至它所裝載的視窗。 如果您主控[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]直接控制，您會收到傳送至控制項的內部訊息迴圈的訊息。 您可以顯示控制項並將訊息傳送給它，但收不到控制項傳送至其父視窗的通知。 這表示，除此之外，您偵測不到使用者何時與控制項互動。 相反地，會建立主視窗，並將控制項設定為該視窗的子系。 這可讓您處理主視窗的訊息，包括控制項傳送給它的通知。 為了方便起見，因為主視窗略高於控制項的簡單包裝函式，所以此套件將稱為 ListBox 控制項。  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>建立主視窗和 ListBox 控制項  
 您可以使用[!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)]來建立和註冊視窗類別，來建立控制項的 [主機] 視窗等等。 不過，比較簡單的方法是使用預先定義的「靜態」視窗類別來建立視窗。 這提供接收來自控制項之通知所需的視窗程序，而且需要最少的程式碼。  
  
 控制項的 HWND 是透過唯讀屬性所公開；因此，主頁面可以使用它，以將訊息傳送至控制項。  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox 控制項會建立為主視窗的子系。 如上面所討論，這兩個視窗的高度和寬度都會設定為傳遞至建構函式的值。 這確保主視窗和控制項的大小與頁面上的保留區域相同。  建立 windows 之後，這個範例會傳回<xref:System.Runtime.InteropServices.HandleRef>物件，其中包含裝載視窗的 HWND。  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>實作 DestroyWindow 和 WndProc  
 除了<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>，您也必須覆寫<xref:System.Windows.Interop.HwndHost.WndProc%2A>和<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>方法<xref:System.Windows.Interop.HwndHost>。 在此範例中，控制項的訊息會由<xref:System.Windows.Interop.HwndHost.MessageHook>處理常式，因此實作<xref:System.Windows.Interop.HwndHost.WndProc%2A>和<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>降至最低。 如果是<xref:System.Windows.Interop.HwndHost.WndProc%2A>，將`handled`至`false`來表示未處理的訊息，並傳回 0。 如<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>，只需終結視窗。  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>在頁面上裝載控制項  
 若要裝載的網頁上的控制項，您先建立的新執行個體`ControlHost`類別。 傳遞的高度和寬度，包含控制項的框線項目 (`ControlHostElement`) 至`ControlHost`建構函式。 這確保 ListBox 的大小正確。 然後主控網頁上的控制項指派`ControlHost`物件<xref:System.Windows.Controls.Decorator.Child%2A>主機屬性<xref:System.Windows.Controls.Border>。  
  
 此範例會將附加的處理常式，以<xref:System.Windows.Interop.HwndHost.MessageHook>事件`ControlHost`控制項從接收訊息。 針對傳送至裝載之視窗的每個訊息，都會引發此事件。 在此情況下，這些是傳送至包裝實際 ListBox 控制項之視窗的訊息，包括來自控制項的通知。 此範例會呼叫 SendMessage 以從控制項取得資訊，並修改其內容。 下節討論頁面如何與控制項進行通訊的詳細資料。  
  
> [!NOTE]
>  請注意，有兩個[!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)]SendMessage 的宣告。 這是必要的因為其中一個使用`wParam`傳遞字串和其他參數會使用它來傳遞整數。 每個簽章都必須要有不同的宣告，確保正確地封送處理資料。  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>實作控制項與頁面之間的通訊  
 您傳送操作控制項[!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]訊息。 在使用者透過將通知傳送至其主視窗與控制項互動時，控制項就會通知您。 [裝載 WPF 範例中的 Win32 ListBox 控制項](http://go.microsoft.com/fwlink/?LinkID=159998)範例包括 UI，它會提供數個範例的運作方式：  
  
-   將項目附加至清單。  
  
-   刪除清單中選取的項目  
  
-   顯示目前所選取項目的文字。  
  
-   顯示清單中的項目數。  
  
 使用者也可以選取項目在清單方塊中按一下，就如同針對傳統[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]應用程式。 每次使用者透過選取、新增或附加項目來變更清單方塊的狀態時，都會更新顯示的資料。  
  
 若要附加項目，請將 LB_ADDSTRING 訊息傳送給清單方塊。 若要刪除項目，請傳送 LB_GETCURSEL 以取得目前選取項目的索引，然後傳送 LB_DELETESTRING 以刪除項目。 此範例也會傳送 LB_GETCOUNT，並使用所傳回的值來更新可顯示項目數的顯示。 SendMessage 這兩個這些執行個體使用其中一種[!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)]前一節中所討論的宣告。  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 當使用者選取的項目或變更其選取項目時，此控制項主控視窗會傳送通知它 WM_COMMAND 訊息，這會引發<xref:System.Windows.Interop.HwndHost.MessageHook>網頁事件。 處理常式會接收與主視窗的主要視窗程序相同的資訊。 它也會將布林值，參考傳遞`handled`。 您設定`handled`至`true`，表示您已處理訊息，而且需要進行任何處理。  
  
 會基於各種原因傳送 WM_COMMAND，因此，您必須檢查通知識別碼來判斷它是否為您要處理的事件。 高的文字中包含識別碼`wParam`參數。 因為[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]沒有 HIWORD 巨集，此範例會使用位元運算子中擷取的識別碼。 如果使用者已建立或變更其選取項目，則識別碼會是 LBN_SELCHANGE。  
  
 收到 LBN_SELCHANGE 時，此範例會將 LB_GETCURSEL 訊息傳送給控制項，以取得所選取項目的索引。 若要取得的文字，您先建立<xref:System.Text.StringBuilder>。 您接著會將 LB_GETTEXT 訊息傳送給控制項。 傳遞空<xref:System.Text.StringBuilder>物件當做`wParam`參數。 當傳回 SendMessage、<xref:System.Text.StringBuilder>會包含所選項目的文字。 這種使用 SendMessage 還需要另一個[!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)]宣告。  
  
 最後，設定`handled`至`true`表示已處理訊息。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Interop.HwndHost>  
 [WPF 和 Win32 交互操作](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [逐步解說：我的第一個 WPF 傳統型應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)
