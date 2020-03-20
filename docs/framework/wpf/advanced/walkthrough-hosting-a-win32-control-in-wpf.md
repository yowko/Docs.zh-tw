---
title: 在 WPF 中託管 Win32 控制項
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: 5185e60640c652b79bd105db54830ac3acc57129
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186745"
---
# <a name="walkthrough-host-a-win32-control-in-wpf"></a>演練：在 WPF 中託管 Win32 控制項
Windows 演示基礎 （WPF） 為創建應用程式提供了豐富的環境。 但是，當您對 Win32 代碼進行大量投資時，在 WPF 應用程式中至少重用其中一些代碼，而不是完全重寫它可能更有效。 WPF 提供了一種在 WPF 頁面上託管 Win32 視窗的簡單機制。  
  
 本主題將引導您完成一個應用程式，[在 WPF 示例中託管 Win32 ListBox 控制項](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)，該應用程式託管 Win32 清單方塊控制項。 此常規過程可以擴展到託管任何 Win32 視窗。  

<a name="requirements"></a>
## <a name="requirements"></a>需求  
 本主題假定對 WPF 和 Windows API 程式設計基本熟悉。 有關 WPF 程式設計的基本介紹，請參閱[入門](../getting-started/index.md)。 有關 Windows API 程式設計的介紹，請參閱有關該主題的眾多書籍中的任何一本書，特別是查理斯·佩佐德的*程式設計 Windows。*  
  
 由於本主題附帶的示例在 C# 中實現，因此它利用平台叫用服務 （PInvoke） 訪問 Windows API。 對 PInvoke 的熟悉是有説明的，但不是必須的。  
  
> [!NOTE]
> 本主題包含一些來自相關聯範例的程式碼範例。 不過，為了方便閱讀，並未包含完整的範例程式碼。 您可以在[WPF 示例中從承載 Win32 ListBox 控制項](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)獲取或查看完整的代碼。  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>基本程序  
 本節概述了在 WPF 頁面上託管 Win32 視窗的基本過程。 其餘各節將說明每個步驟的詳細資料。  
  
 基本裝載程序如下︰  
  
1. 實現 WPF 頁以承載視窗。 一種技術是創建一<xref:System.Windows.Controls.Border>個元素來為託管視窗保留頁面的一部分。  
  
2. 實現類以承載從<xref:System.Windows.Interop.HwndHost>繼承的控制項。  
  
3. 在該類中<xref:System.Windows.Interop.HwndHost>，重寫類成員<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>。  
  
4. 將託管視窗創建為包含 WPF 頁的視窗的子視窗。 儘管傳統的 WPF 程式設計不需要顯式使用它，但託管頁是具有控制碼 （HWND） 的視窗。 通過`hwndParent`<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>方法的參數接收頁面 HWND。 裝載的視窗應該建立為此 HWND 的子系。  
  
5. 建立主視窗之後，即會傳回裝載之視窗的 HWND。 如果要承載一個或多個 Win32 控制項，通常創建主機視窗作為 HWND 的子級，並創建該主機視窗的控制項子級。 在主機視窗中包裝控制項為 WPF 頁提供了一種從控制項接收通知的簡單方法，該控制項處理 HWND 邊界通知的一些特定 Win32 問題。  
  
6. 處理傳送至主視窗的已選取訊息，例如來自子控制項的通知。 做法有二種。  
  
    - 如果希望處理託管類中的消息，請重寫<xref:System.Windows.Interop.HwndHost.WndProc%2A><xref:System.Windows.Interop.HwndHost>類的方法。  
  
    - 如果希望 WPF 處理消息，請處理代碼後面的<xref:System.Windows.Interop.HwndHost>類<xref:System.Windows.Interop.HwndHost.MessageHook>事件。 針對裝載的視窗接收到的每個訊息，都會發生此事件。 如果選擇此選項，則仍必須重寫<xref:System.Windows.Interop.HwndHost.WndProc%2A>，但只需要最少的實現。  
  
7. 重寫<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>的<xref:System.Windows.Interop.HwndHost.WndProc%2A>和<xref:System.Windows.Interop.HwndHost> 您必須重寫這些方法才能滿足協定，<xref:System.Windows.Interop.HwndHost>但可能只需要提供最少的實現。  
  
8. 在代碼背後的檔中，創建控制項宿主類的實例，並將其使其成為旨在承載視窗<xref:System.Windows.Controls.Border>的元素的子級。  
  
9. 通過向託管視窗發送 Microsoft Windows 消息並處理來自其子視窗的消息（如控制項發送的通知）與託管視窗通信。  
  
<a name="page_layout"></a>
## <a name="implement-the-page-layout"></a>實作版面配置  
 承載 ListBox 控制項的 WPF 頁的佈局由兩個區域組成。 頁面的左側承載多個 WPF 控制項，這些控制項提供[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]允許您操作 Win32 控制項的 控制項。 頁面的右上角具有 ListBox 託管控制項的方形區域。  
  
 實現此佈局的代碼非常簡單。 根項目是<xref:System.Windows.Controls.DockPanel>具有兩個子項目的 。 第一個是<xref:System.Windows.Controls.Border>承載 ListBox 控制項的元素。 它會佔用頁面右上角的 200x200 方形。 第二個是包含<xref:System.Windows.Controls.StackPanel>一組 WPF 控制項的元素，該控制項顯示資訊，並允許您通過設置公開的交互操作屬性來操作 ListBox 控制項。 對於 的每個元素都是<xref:System.Windows.Controls.StackPanel>的子項目，請參閱用於詳細介紹這些元素是什麼或它們做什麼的各種元素的參考材料，這些元素列在下面的示例代碼中，但此處不會解釋（基本交互操作模型不需要其中任何元素，它們提供是為了向示例添加一些交互性）。  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>實作類別以裝載 Microsoft Win32 控制項  
 此範例的核心是實際裝載 ControlHost.cs 控制項的類別。 它繼承自 <xref:System.Windows.Interop.HwndHost>。 建構函式採用兩個參數，高度和寬度，對應于承載 ListBox 控制項<xref:System.Windows.Controls.Border>的元素的高度和寬度。 這些值稍後用於確保控制項的大小與<xref:System.Windows.Controls.Border>元素匹配。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 還有一組常數。 這些常量大部分取自 Winuser.h，允許您在調用 Win32 函數時使用傳統名稱。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>覆寫 BuildWindowCore 以建立 Microsoft Win32 視窗  
 重寫此方法以創建將由頁面承載的 Win32 視窗，並在視窗和頁面之間建立連接。 因為此範例包含裝載 ListBox 控制項，所以會建立兩個視窗。 第一個是 WPF 頁實際承載的視窗。 ListBox 控制項會建立為該視窗的子系。  
  
 此方法的原因是要簡化接收來自控制項之通知的程序。 該<xref:System.Windows.Interop.HwndHost>類允許您處理發送到它所承載的視窗的消息。 如果直接承載 Win32 控制項，則會收到發送到控制項的內部訊息迴圈的消息。 您可以顯示控制項並將訊息傳送給它，但收不到控制項傳送至其父視窗的通知。 這表示，除此之外，您偵測不到使用者何時與控制項互動。 相反地，會建立主視窗，並將控制項設定為該視窗的子系。 這可讓您處理主視窗的訊息，包括控制項傳送給它的通知。 為了方便起見，因為主視窗略高於控制項的簡單包裝函式，所以此套件將稱為 ListBox 控制項。  
  
<a name="create_the_window_and_listbox"></a>
#### <a name="create-the-host-window-and-listbox-control"></a>建立主視窗和 ListBox 控制項  
 可以使用 PInvoke 通過創建和註冊視窗類等為控制項創建主機視窗。 不過，比較簡單的方法是使用預先定義的「靜態」視窗類別來建立視窗。 這提供接收來自控制項之通知所需的視窗程序，而且需要最少的程式碼。  
  
 控制項的 HWND 是透過唯讀屬性所公開；因此，主頁面可以使用它，以將訊息傳送至控制項。  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox 控制項會建立為主視窗的子系。 如上面所討論，這兩個視窗的高度和寬度都會設定為傳遞至建構函式的值。 這確保主視窗和控制項的大小與頁面上的保留區域相同。  創建視窗後，該示例將返回包含<xref:System.Runtime.InteropServices.HandleRef>主機視窗的 HWND 的物件。  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>
### <a name="implement-destroywindow-and-wndproc"></a>實作 DestroyWindow 和 WndProc  
 除了 之外<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>，還必須重寫 的<xref:System.Windows.Interop.HwndHost.WndProc%2A><xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A><xref:System.Windows.Interop.HwndHost>和 方法。 在此示例中，控制項的消息由<xref:System.Windows.Interop.HwndHost.MessageHook>處理常式處理，因此 ，<xref:System.Windows.Interop.HwndHost.WndProc%2A><xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>的實現是最小的。 在 中<xref:System.Windows.Interop.HwndHost.WndProc%2A>，設置為`handled``false`指示消息未處理，並返回 0。 對於<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>，只需破壞視窗。  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>
## <a name="host-the-control-on-the-page"></a>在頁面上裝載控制項  
 要在頁面上承載控制項，請首先創建`ControlHost`類的新實例。 將包含控制項 （`ControlHostElement`） 的邊框元素的高度和寬度傳遞給`ControlHost`建構函式。 這確保 ListBox 的大小正確。 然後，通過將物件`ControlHost`<xref:System.Windows.Controls.Decorator.Child%2A>分配給主機<xref:System.Windows.Controls.Border>的屬性，在頁面上託管控制項。  
  
 該示例將處理常式附加到<xref:System.Windows.Interop.HwndHost.MessageHook>`ControlHost`要從控制項接收消息的事件。 針對傳送至裝載之視窗的每個訊息，都會引發此事件。 在此情況下，這些是傳送至包裝實際 ListBox 控制項之視窗的訊息，包括來自控制項的通知。 此範例會呼叫 SendMessage 以從控制項取得資訊，並修改其內容。 下節討論頁面如何與控制項進行通訊的詳細資料。  
  
> [!NOTE]
> 請注意，有兩個 PInvoke 聲明用於發送消息。 這是必需的，因為一個使用`wParam`參數傳遞字串，另一個使用它傳遞整數。 每個簽章都必須要有不同的宣告，確保正確地封送處理資料。  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>
## <a name="implement-communication-between-the-control-and-the-page"></a>實作控制項與頁面之間的通訊  
 通過向控制項發送 Windows 消息來操作該控制項。 在使用者透過將通知傳送至其主視窗與控制項互動時，控制項就會通知您。 [在 WPF 示例中託管 Win32 ListBox 控制項](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)包括一個 UI，它提供了幾個示例，說明其工作原理：  
  
- 將項目附加至清單。  
  
- 刪除清單中選取的項目  
  
- 顯示目前所選取項目的文字。  
  
- 顯示清單中的項目數。  
  
 使用者還可以通過按一下清單方塊中的專案來選擇該專案，就像對於傳統的 Win32 應用程式一樣。 每次使用者透過選取、新增或附加項目來變更清單方塊的狀態時，都會更新顯示的資料。  
  
 要追加專案，請將清單方塊發送[`LB_ADDSTRING`一條消息](/windows/desktop/Controls/lb-addstring)。 要刪除專案，請[`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel)發送以獲取當前選擇的索引，然後[`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring)刪除該專案。 該示例還發送[`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)，並使用返回的值更新顯示項數的顯示。 這兩個實例[`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage)都使用上一節中討論的 PInvoke 聲明之一。  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 當使用者選擇專案或更改其選擇時，控制項通過向宿主視窗[`WM_COMMAND`發送消息來通知](/windows/desktop/menurc/wm-command)主機視窗，這將引發頁面<xref:System.Windows.Interop.HwndHost.MessageHook>的事件。 處理常式會接收與主視窗的主要視窗程序相同的資訊。 它還傳遞對布林值的`handled`引用。 您設置為`handled``true`指示已處理消息，無需進一步處理。  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)發送的原因有多種，因此您必須檢查通知 ID 以確定它是否是您希望處理的事件。 ID 包含在`wParam`參數的高字中。 該示例使用位運算子提取 ID。 如果使用者已創建或更改其選擇，則 ID 將為[`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange)。  
  
 收到[`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange)時，示例通過向控制項[`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel)發送消息來獲取所選項的索引。 要獲取文本，請首先創建 一<xref:System.Text.StringBuilder>個 。 然後，向控制項[`LB_GETTEXT`發送消息。](/windows/desktop/Controls/lb-gettext) 將空<xref:System.Text.StringBuilder>物件作為參數傳遞`wParam`。 返回[`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage)時，<xref:System.Text.StringBuilder>將包含所選項的文本。 這種使用[`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage)需要另一個 PInvoke 聲明。  
  
 最後，設置為`handled``true`指示消息已處理。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.HwndHost>
- [WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)
- [逐步解說：我的第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
