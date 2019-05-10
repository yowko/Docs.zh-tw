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
ms.openlocfilehash: 2cfd8699afe48cb936ecf600c47508ef45781b43
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605508"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>逐步解說：將 Win32 控制項裝載在 WPF 中
Windows Presentation Foundation (WPF) 提供豐富的環境，以建立應用程式。 不過，當您已長期開發 Win32 程式碼中，它可能會重複使用至少一些更有效率的 WPF 應用程式中的程式碼而不是完全重寫程式。 WPF 提供簡單的機制，以裝載 Win32 視窗中，WPF 頁面上。  
  
 本主題將逐步引導您透過應用程式，[裝載 Win32 ListBox 控制項中 WPF 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)，主機 Win32 清單方塊控制項。 此一般程序可以延伸到裝載任何 Win32 視窗中。  

<a name="requirements"></a>   
## <a name="requirements"></a>需求  
 本主題假設基本的熟悉 WPF 和 Windows API 的程式設計。 如需基本 WPF 程式設計簡介，請參閱 <<c0> [ 開始使用](../getting-started/index.md)。 Windows API 程式設計簡介，請參閱任何書籍，特別*程式設計 Windows* Charles petzold 的。  
  
 因為隨附本主題的範例中實作C#，它會使用平台引動服務 (PInvoke) 來存取 Windows API。 PInvoke 疐裾是很有幫助，但並非必要。  
  
> [!NOTE]
>  本主題包含一些來自相關聯範例的程式碼範例。 不過，為了方便閱讀，並未包含完整的範例程式碼。 您可以取得，或檢視的完整程式碼[裝載 Win32 ListBox 控制項中 WPF 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)。  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>基本程序  
 本節將概述裝載 WPF 頁面上的 [Win32] 視窗的基本程序。 其餘各節將說明每個步驟的詳細資料。  
  
 基本裝載程序如下︰  
  
1. 實作 WPF 頁面來裝載視窗。 一種技術是建立<xref:System.Windows.Controls.Border>項目來保留一段所裝載之視窗的頁面。  
  
2. 實作類別以裝載繼承自控制項<xref:System.Windows.Interop.HwndHost>。  
  
3. 在該類別中，覆寫<xref:System.Windows.Interop.HwndHost>類別成員<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>。  
  
4. 裝載的視窗建立為包含 WPF 頁面的視窗的子系。 雖然傳統的 WPF 程式設計不需要明確地將使用它，在裝載頁面是具有的控制代碼 (HWND) 的視窗。 接收頁面 HWND 透過`hwndParent`參數<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>方法。 裝載的視窗應該建立為此 HWND 的子系。  
  
5. 建立主視窗之後，即會傳回裝載之視窗的 HWND。 如果您想要裝載一或多個 Win32 控制項，您通常建立主視窗作為 HWND 的子系，並進行該主視窗的控制項子系。 在主視窗中包裝控制項可提供簡單的方法，讓您 WPF 頁面接收來自控制項，告知其處理跨 HWND 界限的一些特定的 Win32 問題與通知。  
  
6. 處理傳送至主視窗的已選取訊息，例如來自子控制項的通知。 執行這項作業的方法有兩種。  
  
    - 如果您想要處理裝載類別中的訊息，覆寫<xref:System.Windows.Interop.HwndHost.WndProc%2A>方法的<xref:System.Windows.Interop.HwndHost>類別。  
  
    - 如果您想要讓 WPF 處理的訊息，請處理<xref:System.Windows.Interop.HwndHost>類別<xref:System.Windows.Interop.HwndHost.MessageHook>中您的程式碼後置事件。 針對裝載的視窗接收到的每個訊息，都會發生此事件。 如果您選擇此選項時，您仍然必須覆寫<xref:System.Windows.Interop.HwndHost.WndProc%2A>，但您只需要最少的實作。  
  
7. 覆寫<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>並<xref:System.Windows.Interop.HwndHost.WndProc%2A>方法<xref:System.Windows.Interop.HwndHost>。 您必須覆寫這些方法才能滿足<xref:System.Windows.Interop.HwndHost>合約，但您可能只需要提供最簡單的實作。  
  
8. 在程式碼後置檔案中，建立控制項裝載類別的執行個體，並讓它的子系<xref:System.Windows.Controls.Border>要裝載視窗的項目。  
  
9. 與裝載的視窗通訊傳送[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]訊息和來自其子視窗，例如控制項所傳送的通知處理訊息。  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>實作版面配置  
 裝載 ListBox 控制項 [WPF] 頁面的版面配置是由兩個區域所組成。 頁面左側裝載數個 WPF 控制項，可提供[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]，可讓您管理的 Win32 控制項。 頁面的右上角具有 ListBox 託管控制項的方形區域。  
  
 若要實作此版面配置的程式碼都非常簡單。 根項目是<xref:System.Windows.Controls.DockPanel>具有兩個子項目。 第一個是<xref:System.Windows.Controls.Border>裝載 ListBox 控制項項目。 它會佔用頁面右上角的 200x200 方形。 第二個是<xref:System.Windows.Controls.StackPanel>元素，其中包含一組 WPF 控制項來顯示資訊，以及可讓您藉由設定操控 ListBox 控制項公開的交互操作屬性。 每個項目子系的<xref:System.Windows.Controls.StackPanel>，看到用於這些項目是什麼，或其功用的詳細資料的各種元素的參考資料，這些會列在下列範例程式碼，但是無法在這裡說明 （基本交互操作的模型不需要任何一個，他們會提供加入此範例中的某些互動性）。  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>實作類別以裝載 Microsoft Win32 控制項  
 此範例的核心是實際裝載 ControlHost.cs 控制項的類別。 它繼承自<xref:System.Windows.Interop.HwndHost>。 建構函式會採用兩個參數、 高度和寬度，這會對應到的高度和寬度<xref:System.Windows.Controls.Border>裝載 ListBox 控制項項目。 這些值將稍後用來確保控制相符的項目大小<xref:System.Windows.Controls.Border>項目。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 還有一組常數。 這些常數主要取自 Winuser.h，並可讓您呼叫 Win32 函式時，使用傳統的名稱。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>覆寫 BuildWindowCore 以建立 Microsoft Win32 視窗  
 您覆寫這個方法來建立 Win32 視窗，將會由頁面上，並且讓視窗與頁面之間的連線。 因為此範例包含裝載 ListBox 控制項，所以會建立兩個視窗。 第一個是 WPF 頁面實際裝載的視窗。 ListBox 控制項會建立為該視窗的子系。  
  
 此方法的原因是要簡化接收來自控制項之通知的程序。 <xref:System.Windows.Interop.HwndHost>類別可讓您處理傳送至它所裝載的視窗訊息。 如果主機 Win32 直接控制，您會收到傳送至控制項的內部訊息迴圈的訊息。 您可以顯示控制項並將訊息傳送給它，但收不到控制項傳送至其父視窗的通知。 這表示，除此之外，您偵測不到使用者何時與控制項互動。 相反地，會建立主視窗，並將控制項設定為該視窗的子系。 這可讓您處理主視窗的訊息，包括控制項傳送給它的通知。 為了方便起見，因為主視窗略高於控制項的簡單包裝函式，所以此套件將稱為 ListBox 控制項。  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>建立主視窗和 ListBox 控制項  
 您可以使用 PInvoke 建立控制項的主視窗建立和註冊視窗類別等等。 不過，比較簡單的方法是使用預先定義的「靜態」視窗類別來建立視窗。 這提供接收來自控制項之通知所需的視窗程序，而且需要最少的程式碼。  
  
 控制項的 HWND 是透過唯讀屬性所公開；因此，主頁面可以使用它，以將訊息傳送至控制項。  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox 控制項會建立為主視窗的子系。 如上面所討論，這兩個視窗的高度和寬度都會設定為傳遞至建構函式的值。 這確保主視窗和控制項的大小與頁面上的保留區域相同。  建立之後，此範例會傳回<xref:System.Runtime.InteropServices.HandleRef>物件，其中包含的主視窗的 HWND。  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>實作 DestroyWindow 和 WndProc  
 除了<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>，您也必須覆寫<xref:System.Windows.Interop.HwndHost.WndProc%2A>並<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>方法<xref:System.Windows.Interop.HwndHost>。 在此範例中，控制項的訊息會由<xref:System.Windows.Interop.HwndHost.MessageHook>處理常式，因此實作<xref:System.Windows.Interop.HwndHost.WndProc%2A>和<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>非常少。 情況<xref:System.Windows.Interop.HwndHost.WndProc%2A>，將`handled`到`false`指出 不處理訊息，並傳回 0。 針對<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>，只會終結視窗。  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>在頁面上裝載控制項  
 若要裝載的網頁上的控制項，您先建立的新執行個體`ControlHost`類別。 傳遞的 border 項目，其中包含控制項的寬度與高度 (`ControlHostElement`) 到`ControlHost`建構函式。 這確保 ListBox 的大小正確。 您藉由指派，然後裝載網頁上的控制項`ControlHost`物件至<xref:System.Windows.Controls.Decorator.Child%2A>主機屬性<xref:System.Windows.Controls.Border>。  
  
 此範例會將附加的處理常式<xref:System.Windows.Interop.HwndHost.MessageHook>事件的`ControlHost`以接收來自控制項的訊息。 針對傳送至裝載之視窗的每個訊息，都會引發此事件。 在此情況下，這些是傳送至包裝實際 ListBox 控制項之視窗的訊息，包括來自控制項的通知。 此範例會呼叫 SendMessage 以從控制項取得資訊，並修改其內容。 下節討論頁面如何與控制項進行通訊的詳細資料。  
  
> [!NOTE]
>  請注意，sendmessage 的兩個 PInvoke 宣告。 這是必要的因為其中一個使用`wParam`傳遞字串和其他的參數會使用它來傳遞整數。 每個簽章都必須要有不同的宣告，確保正確地封送處理資料。  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>實作控制項與頁面之間的通訊  
 您可以操作控制項傳送 Windows 訊息。 在使用者透過將通知傳送至其主視窗與控制項互動時，控制項就會通知您。 [裝載在 WPF 中的 Win32 ListBox 控制項](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)範例包含的 UI 提供數個範例，其運作方式：  
  
- 將項目附加至清單。  
  
- 刪除清單中選取的項目  
  
- 顯示目前所選取項目的文字。  
  
- 顯示清單中的項目數。  
  
 使用者也可以選取項目在清單方塊中按一下，就像傳統的 Win32 應用程式。 每次使用者透過選取、新增或附加項目來變更清單方塊的狀態時，都會更新顯示的資料。  
  
 若要附加項目，傳送給清單方塊[`LB_ADDSTRING`訊息](/windows/desktop/Controls/lb-addstring)。 若要刪除的項目，請傳送[ `LB_GETCURSEL` ](/windows/desktop/Controls/lb-getcursel)取得目前的選取範圍的索引，然後[ `LB_DELETESTRING` ](/windows/desktop/Controls/lb-deletestring)刪除項目。 此範例也會傳送[ `LB_GETCOUNT` ](/windows/desktop/Controls/lb-getcount)，並使用傳回的值來更新顯示的項目數的顯示。 兩個的這些執行個體[ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage)使用上一節所述的 PInvoke 宣告的其中一個。  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 當使用者選取的項目，或變更其選取項目時，控制項就會通知主視窗傳送[`WM_COMMAND`訊息](/windows/desktop/menurc/wm-command)，這會引發<xref:System.Windows.Interop.HwndHost.MessageHook>頁面的事件。 處理常式會接收與主視窗的主要視窗程序相同的資訊。 它也會傳遞布林值，參考`handled`。 您設定`handled`至`true`以指出已經處理過訊息，且需要進行任何處理。  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command) 會傳送不同的原因，因此您必須檢查通知識別碼來判斷它是否為您想要處理的事件。 此識別碼包含在的高位文字`wParam`參數。 此範例會使用位元運算子，擷取的識別碼。 如果使用者已經進行，或變更其選取項目，則識別碼會是[ `LBN_SELCHANGE` ](/windows/desktop/Controls/lbn-selchange)。  
  
 當[ `LBN_SELCHANGE` ](/windows/desktop/Controls/lbn-selchange)已收到，範例會取得所選項目的索引傳送控制項[`LB_GETCURSEL`訊息](/windows/desktop/Controls/lb-getcursel)。 若要取得文字，您先建立<xref:System.Text.StringBuilder>。 您接著將控制項傳送[`LB_GETTEXT`訊息](/windows/desktop/Controls/lb-gettext)。 傳遞空<xref:System.Text.StringBuilder>物件做為`wParam`參數。 當[ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage)會傳回<xref:System.Text.StringBuilder>會包含所選項目的文字。 這種使用[ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage)需要另一個 PInvoke 宣告。  
  
 最後，設定`handled`至`true`表示已處理訊息。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.HwndHost>
- [WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)
- [逐步解說：我的第一個 WPF 傳統型應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
