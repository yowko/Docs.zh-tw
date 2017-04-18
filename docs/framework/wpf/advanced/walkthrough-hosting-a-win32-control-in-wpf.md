---
title: "逐步解說：在 WPF 中裝載 Win32 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "將 Win32 控制項裝載在 WPF 中"
  - "Win32 程式碼, WPF 互通"
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 逐步解說：在 WPF 中裝載 Win32 控制項
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。  然而，長期開發 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 程式碼時，更有效的方式是在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中重複使用至少一部分的程式碼，而不是完整地重新撰寫程式碼。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供直接在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面上裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗的機制。  
  
 本主題會逐步說明裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 清單方塊控制項的應用程式[在 WPF 中裝載 Win32 ListBox 控制項範例](http://go.microsoft.com/fwlink/?LinkID=159998) \(英文\)。  您可延伸應用這個通用程序，以裝載任何 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="requirements"></a>   
## 需求  
 本主題假設您已熟悉 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式設計的基本概念。  如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式設計的基本簡介，請參閱[快速入門](../../../../docs/framework/wpf/getting-started/index.md)。  如需 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式設計的簡介，請參考討論此主題的各種書籍，尤其是 Charles Petzold 所著的《*Programming Windows*》。  
  
 由於本主題所附的範例是以 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 實作，因此它會利用[!INCLUDE[TLA#tla_pinvoke](../../../../includes/tlasharptla-pinvoke-md.md)] 來存取 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]。  若能對 [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] 有一定熟悉程度將很有幫助，但並非絕對必要。  
  
> [!NOTE]
>  本主題包括摘錄自相關範例的許多程式碼範例。  不過，為了方便閱讀，此課程並未包含完整的範例程式碼。  您可以從[在 WPF 中裝載 Win32 ListBox 控制項範例](http://go.microsoft.com/fwlink/?LinkID=159998) \(英文\) 取得或檢視完整的程式碼。  
  
<a name="basic_procedure"></a>   
## 基本程序  
 本節概述將 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗裝載在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面上的基本程序。  其餘各節則提供每個步驟的詳細說明。  
  
 基本的裝載程序如下：  
  
1.  實作 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面來裝載視窗。  其中一種方法是建立 <xref:System.Windows.Controls.Border> 項目，保留頁面的某個區段來裝載視窗。  
  
2.  實作類別以裝載繼承自 <xref:System.Windows.Interop.HwndHost> 的控制項。  
  
3.  在該類別中，覆寫 <xref:System.Windows.Interop.HwndHost> 類別成員 <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>。  
  
4.  建立裝載的視窗，做為包含 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面之視窗的子系。  雖然傳統的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式開發不需要明確使用它，但是裝載頁面是具有控制代碼 \(HWND\) 的視窗。  您可透過 <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> 方法的 `hwndParent` 參數接收頁面 HWND。  您必須將裝載的視窗建立成這個 HWND 的子系。  
  
5.  建立裝載視窗之後，請傳回所裝載之視窗的 HWND。  如果要裝載一個或多個 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 控制項，您通常會建立一個裝載視窗做為 HWND 的子系，然後再將控制項變成該裝載視窗的子系。  將控制項包裝在裝載視窗中，可以提供一種簡單的方式，供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面用來接收控制項傳回的通知，以處理跨越 HWND 界限之通知的某些特定 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 問題。  
  
6.  處理傳送至裝載視窗的選定訊息，例如子控制項傳回的通知。  執行這項作業的方法有兩種。  
  
    -   如果您想在自己的裝載類別中處理訊息，請覆寫 <xref:System.Windows.Interop.HwndHost> 方法的 <xref:System.Windows.Interop.HwndHost.WndProc%2A> 方法。  
  
    -   如果您想讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 處理訊息，請在程式碼後置 \(Code\-Behind\) 中處理 <xref:System.Windows.Interop.HwndHost> 類別 <xref:System.Windows.Interop.HwndHost.MessageHook> 事件。  每次裝載的視窗收到訊息時，都會發生這個事件。  如果選擇這個選項，您仍然必須覆寫 <xref:System.Windows.Interop.HwndHost.WndProc%2A>，但是只需要進行最簡單的實作 \(Implementation\)。  
  
7.  覆寫 <xref:System.Windows.Interop.HwndHost> 的 <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> 和 <xref:System.Windows.Interop.HwndHost.WndProc%2A> 方法。  您必須覆寫這些方法以滿足 <xref:System.Windows.Interop.HwndHost> 合約，但是您可能只需要提供最簡單的實作。  
  
8.  在程式碼後置的檔案中，建立控制項裝載類別的執行個體，並將它設為要用來裝載視窗之 <xref:System.Windows.Controls.Border> 項目的子系。  
  
9. 與裝載的視窗進行通訊，方法是將 [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] 訊息傳送至裝載的視窗，並處理其子視窗傳回的訊息，例如控制項所傳送的通知。  
  
<a name="page_layout"></a>   
## 實作頁面配置  
 裝載 ListBox 控制項的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面，其配置由兩個區域組成。  頁面左邊裝載幾個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，提供可用來管理 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 控制項的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。  頁面右上角有一塊方形區域，其中包含裝載的 ListBox 控制項。  
  
 用來實作這個配置的程式碼相當簡單。  其根項目 \(Root Element\) 是具有兩個子項目的 <xref:System.Windows.Controls.DockPanel>。  第一個子項目是裝載 ListBox 控制項的 <xref:System.Windows.Controls.Border> 項目。  這個項目佔用了頁面右上角 200x200 的方形區域。  第二個子項目則是 <xref:System.Windows.Controls.StackPanel> 項目，其中包含一組顯示資訊的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，可以讓您透過設定公開的互通性屬性來管理 ListBox 控制項。  對於 <xref:System.Windows.Controls.StackPanel> 子系的每個項目，如需所用各種項目之定義或功能的詳細資訊，請參閱這些項目的參考資料；下面的範例程式碼雖然列出這些項目，但並未在此加以說明 \(基本的互通模型並不需要其中任何項目；提供這些項目的目的是為了讓範例增加一些互動性\)。  
  
 [!code-xml[WPFHostingWin32Control#WPFUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## 實作類別以裝載 Microsoft Win32 控制項  
 這個範例的核心是實際裝載控制項的類別 ControlHost.cs。  它繼承自 <xref:System.Windows.Interop.HwndHost>。  此建構函式使用高度和寬度兩個參數，而這兩個參數對應於裝載 ListBox 控制項之 <xref:System.Windows.Controls.Border> 項目的高度和寬度。  稍後會使用這些值來確定控制項的大小是否與 <xref:System.Windows.Controls.Border> 項目相符。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 另外還有一組常數。  這些常數大部分都是取自 Winuser.h，而且可以讓您在呼叫 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 函式時使用傳統的名稱。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### 覆寫 BuildWindowCore 以建立 Microsoft Win32 視窗  
 您可以覆寫這個方法，以建立頁面所要裝載的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗，並建立視窗與頁面的連接。  因為這個範例與裝載 ListBox 控制項有關，所以會建立兩個視窗。  第一個視窗是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面實際裝載的視窗。  ListBox 控制項會建立為該視窗的子系。  
  
 使用這種方法的原因是為了簡化從控制項接收通知的程序。  <xref:System.Windows.Interop.HwndHost> 類別可以讓您處理傳送至其所裝載之視窗的訊息。  如果直接裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 控制項，您會收到傳送至該控制項內部迴圈 \(Loop\) 的訊息。  您可以顯示控制項，也可傳送訊息至控制項，但是不會收到控制項傳送給其父視窗的通知。  這表示您將無法偵測使用者何時與控制項互動等各種活動。  因此，請建立裝載視窗，並將控制項設成該視窗的子系。  這可讓您處理裝載視窗的訊息，包括控制項傳送至該視窗的通知。  因為裝載視窗比控制項的簡單包裝函式稍微複雜一點，所以為了方便起見，我們將這個封裝稱為 ListBox 控制項。  
  
<a name="create_the_window_and_listbox"></a>   
#### 建立裝載視窗和 ListBox 控制項  
 您可以使用 [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)]，透過建立及註冊視窗類別等方式，建立控制項的裝載視窗。  不過，比較簡單的方法是使用預先定義的「靜態」視窗類別建立視窗。  除了能夠提供必要的視窗程序供您接收控制項傳回的通知以外，這種方法所需撰寫的程式碼也最少。  
  
 控制項公開 HWND 的方式是透過唯讀屬性，例如可以用它來傳送訊息至控制項的裝載頁面。  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox 控制項會建立為裝載視窗的子系。  這兩個視窗的高度和寬度都會設定為傳遞至上述建構函式的值。  如此便可確保裝載視窗和控制項的大小與頁面上的保留區域相同。  在建立視窗之後，此範例會傳回 <xref:System.Runtime.InteropServices.HandleRef> 物件，其中包含裝載視窗的 HWND。  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### 實作 DestroyWindow 和 WndProc  
 除了 <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> 之外，您還必須覆寫 <xref:System.Windows.Interop.HwndHost> 的 <xref:System.Windows.Interop.HwndHost.WndProc%2A> 和 <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> 方法。  在這個範例中，控制項的訊息是由 <xref:System.Windows.Interop.HwndHost.MessageHook> 處理常式負責處理，因此 <xref:System.Windows.Interop.HwndHost.WndProc%2A> 和 <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> 的實作相當簡單。  在 <xref:System.Windows.Interop.HwndHost.WndProc%2A> 的案例中，請將 `handled` 設定為 `false`，指出未處理訊息並傳回 0。  如果是 <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>，則直接終結視窗。  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## 將控制項裝載在頁面上  
 若要將控制項裝載到頁面上，請先建立 `ControlHost` 類別的執行個體。  請將包含控制項之框線項目 \(`ControlHostElement`\) 的高度和寬度傳遞至 `ControlHost` 建構函式。  這個動作可確保 ListBox 會設定為正確的大小。  接著請將 `ControlHost` 物件指派給裝載 <xref:System.Windows.Controls.Border> 的 <xref:System.Windows.Controls.Decorator.Child%2A> 屬性，以便將控制項裝載在頁面上。  
  
 此範例會將處理常式附加至 `ControlHost` 的 <xref:System.Windows.Interop.HwndHost.MessageHook> 事件，以接收控制項傳回的訊息。  每次有訊息傳送到裝載的視窗時，都會引發這個事件。  在這個案例中，這些訊息是傳送至實際用來包裝 ListBox 控制項之視窗的訊息，包括控制項傳回的通知。  此範例會呼叫 SendMessage 從控制項取得資訊，並修改其內容。  下一節將詳細討論頁面與控制項通訊的方式。  
  
> [!NOTE]
>  請注意，SendMessage 有兩個 [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] 宣告。  這是必要的，因為其中一個會使用 `wParam` 參數來傳遞字串，而另一個則用它來傳遞整數。  每個簽章 \(Signature\) 都需要個別的宣告，以確保資料能夠正確封送處理。  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## 在控制項和頁面之間實作通訊  
 您可透過傳送 [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)] 訊息至控制項來管理控制項。  控制項會在使用者與其互動時傳送通知至其裝載視窗來通知您。  [在 WPF 中裝載 Win32 ListBox 控制項範例](http://go.microsoft.com/fwlink/?LinkID=159998) \(英文\) 包括一個 UI，提供如何執行這項操作的數個範例：  
  
-   將項目附加至清單。  
  
-   從清單刪除選取的項目。  
  
-   顯示目前所選項目的文字。  
  
-   顯示清單中的項目數目。  
  
 使用者也可以按一下以選取清單方塊中的項目，如同在傳統 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 應用程式中一樣。  每次使用者透過選取、加入或附加項目來變更清單方塊的狀態時，顯示的資料都會更新。  
  
 若要附加檔案，請將 LB\_ADDSTRING 訊息傳送至清單方塊。  若要刪除項目，請傳送 LB\_GETCURSEL 以取得目前選取範圍的索引，然後再傳送 LB\_DELETESTRING 來刪除項目。  此範例也會傳送 LB\_GETCOUNT，並使用傳回的值更新顯示項目數目的畫面。  這兩個 SendMessage 執行個體都會使用上一節討論的其中一個 [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] 宣告。  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 當使用者選取項目或變更其選擇時，控制項會傳送 WM\_COMMAND 訊息給裝載視窗來通知它，進而引發頁面的 <xref:System.Windows.Interop.HwndHost.MessageHook> 事件。  處理常式會收到裝載視窗之主要視窗程序所收到的相同資訊。  它也會傳遞布林 \(Boolean\) 值的參考 `handled`。  將 `handled` 設為 `true` 表示您已處理訊息，不需要進行其他處理。  
  
 傳送 WM\_COMMAND 的原因很多，您必須查看通知 ID 來判斷它是不是您想要處理的事件。  這個 ID 包含在 `wParam` 參數的高位文字中。  因為 [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] 沒有 HIWORD 巨集，所以本範例使用位元 \(Bitwise\) 運算子來擷取此 ID。  如果使用者已經做出或變更其選擇，此 ID 便為 LBN\_SELCHANGE。  
  
 收到 LBN\_SELCHANGE 時，此範例會傳送 LB\_GETCURSEL 訊息到控制項，以取得所選項目的索引。  為了取得文字，您會先建立 <xref:System.Text.StringBuilder>，  然後傳送 LB\_GETTEXT 訊息到控制項。  請傳遞空的 <xref:System.Text.StringBuilder> 物件做為 `wParam` 參數。  當 SendMessage 傳回時，<xref:System.Text.StringBuilder> 會包含所選項目的文字。  SendMessage 的這種用法還需要另外一個 [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] 宣告。  
  
 最後，請將 `handled` 設定為 `true`，表示訊息已經過處理。  
  
## 請參閱  
 <xref:System.Windows.Interop.HwndHost>   
 [WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [逐步解說：WPF 使用者入門](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)