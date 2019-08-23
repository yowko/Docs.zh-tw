---
title: 逐步解說：將 Win32 控制項裝載在 WPF 中
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: cc27189afd2185d5f0a1eeacccf4c537dd3d9c2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917535"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>逐步解說：將 Win32 控制項裝載在 WPF 中
Windows Presentation Foundation (WPF) 提供豐富的環境來建立應用程式。 不過, 當您在 Win32 程式碼中投入大量投資時, 在 WPF 應用程式中至少重複使用其中一些程式碼, 而不是完全重新撰寫, 可能會更有效率。 WPF 在 WPF 頁面上提供了直接裝載 Win32 視窗的機制。  
  
 本主題將逐步引導您在裝載 Win32 清單方塊控制項的[WPF 範例中, 裝載 Win32 ListBox 控制項](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)。 這個一般程式可以擴充為裝載任何 Win32 視窗。  

<a name="requirements"></a>   
## <a name="requirements"></a>需求  
 本主題假設您對 WPF 和 Windows API 程式設計有基本的熟悉度。 如需 WPF 程式設計的基本簡介, 請參閱[消費者入門](../getting-started/index.md)。 如需 Windows API 程式設計的簡介, 請參閱主題中的任何一本書, 特別是 Charles Petzold 的程式*設計視窗*。  
  
 由於本主題隨附的範例是在中C#執行, 因此它會使用平台叫用服務 (PInvoke) 來存取 Windows API。 對於 PInvoke 的熟悉程度很有説明, 但並不重要。  
  
> [!NOTE]
> 本主題包含一些來自相關聯範例的程式碼範例。 不過，為了方便閱讀，並未包含完整的範例程式碼。 在 WPF 範例中, 您可以取得或查看[裝載 Win32 ListBox 控制項](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)的完整程式碼。  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>基本程序  
 本節概述在 WPF 頁面上裝載 Win32 視窗的基本程式。 其餘各節將說明每個步驟的詳細資料。  
  
 基本裝載程序如下︰  
  
1. 執行 WPF 頁面來裝載視窗。 其中一個方法是建立一個<xref:System.Windows.Controls.Border>專案, 為裝載的視窗保留頁面的區段。  
  
2. 執行類別來裝載繼承自<xref:System.Windows.Interop.HwndHost>的控制項。  
  
3. 在該類別中, 覆<xref:System.Windows.Interop.HwndHost>寫類別<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>成員。  
  
4. 將裝載的視窗建立為包含 WPF 頁面之視窗的子系。 雖然傳統 WPF 程式設計不需要明確地使用它, 但主控頁面是具有控制碼 (HWND) 的視窗。 您會透過`hwndParent` <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>方法的參數來接收分頁 HWND。 裝載的視窗應該建立為此 HWND 的子系。  
  
5. 建立主視窗之後，即會傳回裝載之視窗的 HWND。 如果您想要裝載一或多個 Win32 控制項, 通常會將主機視窗建立為 HWND 的子系, 並將控制項的子系設為該主控視窗。 將控制項包裝在主機視窗中, 可讓您從控制項接收通知的方式很簡單, 這會處理跨 HWND 界限的通知特定 Win32 問題。  
  
6. 處理傳送至主視窗的已選取訊息，例如來自子控制項的通知。 執行這項作業的方法有兩種。  
  
    - 如果您想要處理裝載類別中的訊息, 請覆<xref:System.Windows.Interop.HwndHost.WndProc%2A>寫<xref:System.Windows.Interop.HwndHost>類別的方法。  
  
    - 如果您想要讓 WPF 處理訊息, 請處理常式代碼<xref:System.Windows.Interop.HwndHost>後<xref:System.Windows.Interop.HwndHost.MessageHook>置中的類別事件。 針對裝載的視窗接收到的每個訊息，都會發生此事件。 如果您選擇此選項, 您仍然必須覆<xref:System.Windows.Interop.HwndHost.WndProc%2A>寫, 但您只需要最少的執行。  
  
7. 覆寫的<xref:System.Windows.Interop.HwndHost.WndProc%2A> <xref:System.Windows.Interop.HwndHost>和方法<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> 。 您必須覆寫這些方法以滿足<xref:System.Windows.Interop.HwndHost>合約, 但您可能只需要提供最基本的執行。  
  
8. 在您的程式碼後置檔案中, 建立控制項裝載類別的實例, 並將它設為<xref:System.Windows.Controls.Border>要裝載視窗的元素子系。  
  
9. 藉由[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]傳送訊息和處理來自其子視窗的訊息 (例如控制項所傳送的通知), 與裝載的視窗進行通訊。  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>實作版面配置  
 主控 ListBox 控制項的 WPF 頁面版面配置包含兩個區域。 頁面的左邊裝載數個 WPF 控制項, 以提供[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]可讓您操作 Win32 控制項的。 頁面的右上角具有 ListBox 託管控制項的方形區域。  
  
 執行此版面配置的程式碼相當簡單。 根項目是<xref:System.Windows.Controls.DockPanel>具有兩個子項目的。 第一個是<xref:System.Windows.Controls.Border>裝載 ListBox 控制項的元素。 它會佔用頁面右上角的 200x200 方形。 第二個是<xref:System.Windows.Controls.StackPanel>專案, 其中包含一組顯示資訊的 WPF 控制項, 並可讓您藉由設定公開的互通性屬性來操作 ListBox 控制項。 針對每個子<xref:System.Windows.Controls.StackPanel>系的專案, 請參閱各種元素的參考資料, 這些專案是用來詳細說明這些元素的用途或其用途, 這些專案會列在下面的範例程式碼中, 但不會在此處說明 (基本互通模型不需要其中任何一項, 而是為了在範例中新增一些互動性而提供。  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>實作類別以裝載 Microsoft Win32 控制項  
 此範例的核心是實際裝載 ControlHost.cs 控制項的類別。 它繼承自 <xref:System.Windows.Interop.HwndHost>。 此函式會採用兩個參數: height 和 width, 其對應至主控 ListBox 控制項<xref:System.Windows.Controls.Border>之專案的高度和寬度。 稍後會使用這些值, 以確保控制項的大小符合<xref:System.Windows.Controls.Border>元素。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 還有一組常數。 這些常數主要取自 Winuser, 並可讓您在呼叫 Win32 函數時使用傳統名稱。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>覆寫 BuildWindowCore 以建立 Microsoft Win32 視窗  
 您會覆寫這個方法, 以建立將由頁面主控的 Win32 視窗, 並在視窗和頁面之間建立連接。 因為此範例包含裝載 ListBox 控制項，所以會建立兩個視窗。 第一個是 WPF 頁面實際裝載的視窗。 ListBox 控制項會建立為該視窗的子系。  
  
 此方法的原因是要簡化接收來自控制項之通知的程序。 <xref:System.Windows.Interop.HwndHost>類別可讓您處理傳送至所裝載之視窗的訊息。 如果您直接裝載 Win32 控制項, 則會收到傳送至控制項內部訊息迴圈的訊息。 您可以顯示控制項並將訊息傳送給它，但收不到控制項傳送至其父視窗的通知。 這表示，除此之外，您偵測不到使用者何時與控制項互動。 相反地，會建立主視窗，並將控制項設定為該視窗的子系。 這可讓您處理主視窗的訊息，包括控制項傳送給它的通知。 為了方便起見，因為主視窗略高於控制項的簡單包裝函式，所以此套件將稱為 ListBox 控制項。  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>建立主視窗和 ListBox 控制項  
 您可以使用 PInvoke 來建立控制項的主視窗, 方法是建立和註冊視窗類別等等。 不過，比較簡單的方法是使用預先定義的「靜態」視窗類別來建立視窗。 這提供接收來自控制項之通知所需的視窗程序，而且需要最少的程式碼。  
  
 控制項的 HWND 是透過唯讀屬性所公開；因此，主頁面可以使用它，以將訊息傳送至控制項。  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox 控制項會建立為主視窗的子系。 如上面所討論，這兩個視窗的高度和寬度都會設定為傳遞至建構函式的值。 這確保主視窗和控制項的大小與頁面上的保留區域相同。  建立 windows 之後, 此範例<xref:System.Runtime.InteropServices.HandleRef>會傳回物件, 其中包含主機視窗的 HWND。  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>實作 DestroyWindow 和 WndProc  
 除了之外<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, 您也必須覆<xref:System.Windows.Interop.HwndHost.WndProc%2A>寫的和<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>方法<xref:System.Windows.Interop.HwndHost>。 在此範例中, 控制項的訊息是由<xref:System.Windows.Interop.HwndHost.MessageHook>處理常式處理, 因此<xref:System.Windows.Interop.HwndHost.WndProc%2A>和<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>的實作為最低。 如果<xref:System.Windows.Interop.HwndHost.WndProc%2A>是, 請將設定`handled`為`false` , 表示未處理訊息, 並傳回0。 針對<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, 只會摧毀視窗。  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>在頁面上裝載控制項  
 若要在頁面上裝載控制項, 請先建立`ControlHost`類別的新實例。 將包含控制項 (`ControlHostElement`) 之 border 元素的高度和寬度傳遞至該`ControlHost`函式。 這確保 ListBox 的大小正確。 然後藉由將`ControlHost`物件指派給主機<xref:System.Windows.Controls.Border>的<xref:System.Windows.Controls.Decorator.Child%2A>屬性, 在頁面上裝載控制項。  
  
 這個範例會將處理常式附加<xref:System.Windows.Interop.HwndHost.MessageHook>至的事件`ControlHost` , 以接收來自控制項的訊息。 針對傳送至裝載之視窗的每個訊息，都會引發此事件。 在此情況下，這些是傳送至包裝實際 ListBox 控制項之視窗的訊息，包括來自控制項的通知。 此範例會呼叫 SendMessage 以從控制項取得資訊，並修改其內容。 下節討論頁面如何與控制項進行通訊的詳細資料。  
  
> [!NOTE]
> 請注意, SendMessage 有兩個 PInvoke 宣告。 這是必要的`wParam` , 因為其中一個使用參數來傳遞字串, 另一個使用它來傳遞整數。 每個簽章都必須要有不同的宣告，確保正確地封送處理資料。  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>實作控制項與頁面之間的通訊  
 您可以藉由傳送 Windows 訊息來操控控制項。 在使用者透過將通知傳送至其主視窗與控制項互動時，控制項就會通知您。 [在 WPF 中裝載 Win32 ListBox 控制項](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)範例包含的 UI 提供了數個範例, 說明其運作方式:  
  
- 將項目附加至清單。  
  
- 刪除清單中選取的項目  
  
- 顯示目前所選取項目的文字。  
  
- 顯示清單中的項目數。  
  
 使用者也可以按一下清單方塊中的專案, 就像是傳統的 Win32 應用程式一樣。 每次使用者透過選取、新增或附加項目來變更清單方塊的狀態時，都會更新顯示的資料。  
  
 若要附加專案, 請傳送[ `LB_ADDSTRING`訊息](/windows/desktop/Controls/lb-addstring)給清單方塊。 若要刪除專案, [`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel)請傳送以取得目前選取範圍的索引, [`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring)然後刪除專案。 此範例也[`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)會傳送, 並使用傳回的值來更新顯示專案數的顯示。 這兩個實例[`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage)都使用上一節中所討論的其中一個 PInvoke 宣告。  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 當使用者選取專案或變更其選擇時, 控制項會傳送[ `WM_COMMAND`訊息](/windows/desktop/menurc/wm-command)給主視窗<xref:System.Windows.Interop.HwndHost.MessageHook> , 以引發頁面的事件。 處理常式會接收與主視窗的主要視窗程序相同的資訊。 它也會傳遞布林值`handled`的參考。 您將`handled`設定`true`為, 以指出您已處理訊息, 且不需要進一步處理。  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)基於各種原因而傳送, 因此您必須檢查通知識別碼, 以判斷它是否為您想要處理的事件。 此識別碼包含在`wParam`參數的最大字組中。 此範例會使用位運算子來將識別碼解壓縮。 如果使用者已做出或變更其選擇, 則識別碼會是[`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange)。  
  
 當[`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange)收到時, 範例會藉由傳送[ `LB_GETCURSEL`訊息](/windows/desktop/Controls/lb-getcursel)給控制項, 取得所選取專案的索引。 若要取得文字, 您必須先建立<xref:System.Text.StringBuilder>。 接著, 您可以傳送[ `LB_GETTEXT`訊息](/windows/desktop/Controls/lb-gettext)給控制項。 傳遞空<xref:System.Text.StringBuilder>的物件`wParam`做為參數。 當[`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage)傳回時<xref:System.Text.StringBuilder> , 將包含所選取專案的文字。 這種[`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage)用法還需要另一個 PInvoke 宣告。  
  
 最後, 將`handled`設定`true`為, 表示已處理訊息。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.HwndHost>
- [WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)
- [逐步解說：我的第一個 WPF 傳統型應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
