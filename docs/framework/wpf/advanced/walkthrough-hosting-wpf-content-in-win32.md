---
title: "逐步解說：在 Win32 中裝載 WPF 內容 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "將 WPF 內容裝載在 Win32 視窗中"
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 逐步解說：在 Win32 中裝載 WPF 內容
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。  不過，如果您已長期開發 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 程式碼，將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能加入應用程式，可能會比重寫原始程式碼更有效率。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供簡單的機制，可在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。  
  
 本教學課程說明如何撰寫範例應用程式：[在 Win32 視窗中裝載 WPF 內容的範例](http://go.microsoft.com/fwlink/?LinkID=160004)，以在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。  您可以擴充這個範例，以裝載任何 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗。  因為這牽涉到混合 Managed 和 Unmanaged程式碼，所以是以 [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] 撰寫應用程式。  
  
   
  
<a name="requirements"></a>   
## 需求  
 本教學課程假設您對 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式設計已有基本的熟悉度。  如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式設計的基本簡介，請參閱[快速入門](../../../../docs/framework/wpf/getting-started/index.md)。  如需 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式設計的簡介，您應參考有關該主旨的任何書籍，這類書籍很多，請特別參考 Charles Petzold 的《 Windows 程式設計》\(Programming Windows\)。  
  
 由於隨附此教學課程的範例是在 [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] 中實作，因此本教學課程假設您已熟悉如何使用 [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] 來設計 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 程式，並且了解 Managed 程式碼的程式設計。  熟悉 [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] 會有幫助，但並非必要。  
  
> [!NOTE]
>  本教學課程包含一些來自相關範例的程式碼範例。  不過，為了方便閱讀，並未包含完整的範例程式碼。  如需完整的範例程式碼，請參閱 [在 Win32 視窗中裝載 WPF 內容的範例](http://go.microsoft.com/fwlink/?LinkID=160004)。  
  
<a name="basic_procedure"></a>   
## 基本程序  
 本節概述在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的基本程序。  其餘各節將說明每個步驟的詳細資訊。  
  
 在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗上裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的關鍵是 <xref:System.Windows.Interop.HwndSource> 類別。  這個類別會包裝 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容，使其併入 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中，做為子視窗。  下列方法會將 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 合併在單一應用程式中。  
  
1.  將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容實作成 Managed 類別。  
  
2.  以 [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] 實作 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 應用程式。  如果您是使用現有的應用程式和 Unmanaged [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] 程式碼開始進行，通常只要變更專案設定來包含 `/clr` 編譯器旗標，該應用程式就可以呼叫 Managed 程式碼。  
  
3.  將執行緒模型設為單一執行緒 Apartment \(STA\)。  
  
4.  處理視窗程序中的 [WM\_CREATE](http://msdn.microsoft.com/library/ms632619.aspx) 通知，並執行下列動作：  
  
    1.  以父視窗做為 `parent` 參數，建立新的 <xref:System.Windows.Interop.HwndSource> 物件。  
  
    2.  建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容類別的執行個體。  
  
    3.  將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容物件的參考指派給 <xref:System.Windows.Interop.HwndSource> 的 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> 屬性。  
  
    4.  取得內容的 HWND。  <xref:System.Windows.Interop.HwndSource> 物件的 <xref:System.Windows.Interop.HwndSource.Handle%2A> 屬性包含視窗控制代碼 \(HWND\)。  若要取得可用於應用程式 Unmanaged 部分的 HWND，請將 `Handle.ToPointer()` 轉型為 HWND。  
  
5.  實作 Managed 類別，其中包含靜態欄位來保存 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的參考。  這個類別可讓您從 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式碼取得 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的參考。  
  
6.  將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容指派至靜態欄位。  
  
7.  將處理常式附加到一或多個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件，以接收 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的通知。  
  
8.  使用儲存在靜態欄位中的參考來設定屬性等等，以與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容通訊。  
  
> [!NOTE]
>  您也可以使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 來實作 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。  不過，您必須另外將它編譯成 [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]，並從 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 應用程式參考該 [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]。  此程序的其餘部分與上述類似。  
  
<a name="implementing_the_application"></a>   
## 實作主應用程式  
 本節描述如何在基本 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 應用程式中裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。  內容本身實作在 [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] 中，做為 Managed 類別。  大部分的情況下，這就是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式設計。  [實作 WPF 內容](#implementing_the_wpf_page)中將會討論內容實作的關鍵環節。  
  
<a name="autoNestedSectionsOUTLINE1"></a>   
-   [基本應用程式](#the_basic_application)  
  
-   [裝載 WPF 內容](#hosting_the_wpf_page)  
  
-   [保存 WPF 內容的參考](#holding_a_reference)  
  
-   [與 WPF 內容通訊](#communicating_with_the_page)  
  
<a name="the_basic_application"></a>   
### 基本應用程式  
 主應用程式的起點是建立 [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] 範本。  
  
1.  開啟 [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)]，再從 \[檔案\] 功能表選取 \[新增專案\]。  
  
2.  從 [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] 專案類型的清單選取 \[Win32\]。  如果您的預設語言不是 [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)]，您會在 \[其他語言\] 底下找到這些專案類型。  
  
3.  選取 \[Win32 專案\] 範本，為專案指派名稱，然後按一下 \[確定\]，以啟動 \[Win32 應用程式精靈\]。  
  
4.  接受精靈的預設設定，然後按一下 \[完成\] 來啟動專案。  
  
 此範本會建立基本 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 應用程式，包括：  
  
-   應用程式的進入點。  
  
-   視窗，具有相關聯的視窗程序 \(WndProc\)。  
  
-   含有 \[檔案\] 和 \[說明\] 標題的功能表。  \[檔案\] 功能表有 \[結束\] 項目，可關閉應用程式。  \[說明\] 功能表有 \[關於\] 項目，可啟動簡單的對話方塊。  
  
 在您開始撰寫程式碼來裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容之前，您必須先對基本範本進行兩個修改。  
  
 第一個是將專案編譯成 Managed 程式碼。  根據預設，專案會編譯成 Unmanaged 程式碼。  不過，因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是以 Managed 程式碼實作，所以專案必須據以編譯。  
  
1.  在 \[方案總管\] 中，以滑鼠右鍵按一下專案名稱，然後從內容功能表選取 \[屬性\]，以啟動 \[屬性頁\] 對話方塊。  
  
2.  在左窗格中，從樹狀檢視選取 \[組態屬性\]。  
  
3.  在右窗格中，從 \[專案預設值\] 清單選取 \[Common Language Runtime\] 支援。  
  
4.  從下拉式清單方塊選取 \[Common Language Runtime 支援 \(\/clr\)\]。  
  
> [!NOTE]
>  此編譯器旗標可讓您在應用程式中使用 Managed 程式碼，但 Unmanaged 程式碼還是會編譯成和之前一樣。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用單一執行緒 Apartment \(STA\) 執行緒模型。  為了與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容程式碼正常搭配運作，您必須將屬性套用至進入點，以將應用程式的執行緒模型設為 STA。  
  
 [!code-cpp[Win32HostingWPFPage#WinMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]  
  
<a name="hosting_the_wpf_page"></a>   
### 裝載 WPF 內容  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容是簡單的位址輸入應用程式。  它包含數個 <xref:System.Windows.Controls.TextBox> 控制項，以取得使用者名稱、位址等等。  另外還有兩個 <xref:System.Windows.Controls.Button> 控制項：\[確定\] 和 \[取消\]。  當使用者按一下 \[確定\]，按鈕的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式就會從 <xref:System.Windows.Controls.TextBox> 控制項收集資料、將資料指派給對應的屬性，並引發自訂事件 `OnButtonClicked`。  當使用者按一下 \[取消\]，處理常式就只會引發 `OnButtonClicked`。   `OnButtonClicked` 的事件引數物件包含布林值的欄位，指出所點選的按鈕。  
  
 裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的程式碼在主視窗上 [WM\_CREATE](http://msdn.microsoft.com/library/ms632619.aspx) 通知的處理常式中實作。  
  
 [!code-cpp[Win32HostingWPFPage#WMCreate](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]  
  
 `GetHwnd` 方法會採用大小和位置資訊，再加上父視窗控制代碼，並傳回所裝載之 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的視窗控制代碼。  
  
> [!NOTE]
>  您不能將 `#using` 指示詞用於 `System::Windows::Interop` 命名空間。  這麼做會在該命名空間中的 <xref:System.Windows.Interop.MSG> 結構與 winuser.h 中宣告的 MSG 結構之間，造成名稱衝突。  您必須改用完整的名稱來存取該命名空間的內容。  
  
 [!code-cpp[Win32HostingWPFPage#GetHwnd](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]  
  
 您不能將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容直接裝載在應用程式視窗中。  相反地，您要先建立 <xref:System.Windows.Interop.HwndSource> 物件來包裝 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。  此物件基本上就是設計用來裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的視窗。  若要將 <xref:System.Windows.Interop.HwndSource> 物件裝載在父視窗中，您可以將該物件建立成應用程式中 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗的子系。  <xref:System.Windows.Interop.HwndSource> 建構函式參數所包含的資訊，與您建立 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 子視窗時，傳遞至 CreateWindow 的資訊類似。  
  
 您接下來要建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容物件的執行個體。  在此案例中，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容使用 [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] 來實作成個別的類別 `WPFPage`。  您也可以使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來實作 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。  不過，若要這麼做，您需要設定個別的專案，並將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容建置成 [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]。  您可以將該 [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] 的參考加入您的專案，並使用該參考來建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的執行個體。  
  
 您要將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的參考指派給 <xref:System.Windows.Interop.HwndSource> 的 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> 屬性，以在子視窗中顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。  
  
 下一行程式碼會將事件處理常式 `WPFButtonClicked` 附加至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容 `OnButtonClicked` 事件。  當使用者按一下 \[確定\] 或 \[取消\] 按鈕，就會呼叫此處理常式。  請參閱 [communicating\_with\_the\_WPF content](#communicating_with_the_page)，以取得此事件處理常式的進一步討論。  
  
 所顯示的最後一行程式碼會傳回與 <xref:System.Windows.Interop.HwndSource> 物件相關聯的視窗控制代碼 \(HWND\)。  您可以從 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式碼使用此控制代碼，將訊息傳送至裝載的視窗，但此範例並沒有這麼做。  <xref:System.Windows.Interop.HwndSource> 物件每次收到訊息時，都會引發事件。  若要處理這些訊息，請呼叫 <xref:System.Windows.Interop.HwndSource.AddHook%2A> 方法來附加訊息處理常式，然後在該處理常式中處理訊息。  
  
<a name="holding_a_reference"></a>   
### 保存 WPF 內容的參考  
 就許多應用程式而言，您稍後會想要與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容通訊。  例如，您可能會想要修改 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容屬性，或是讓 <xref:System.Windows.Interop.HwndSource> 物件裝載不同的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。  若要這麼做，您需要 <xref:System.Windows.Interop.HwndSource> 物件或 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的參考。  <xref:System.Windows.Interop.HwndSource> 物件及其相關聯的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容會保留在記憶體中，直到您終結視窗控制代碼。  不過，一旦您從視窗程序返回，您指派給 <xref:System.Windows.Interop.HwndSource> 物件的變數就會超出範圍。  若要以自訂方式來處理 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 應用程式的這個問題，您可以使用靜態或全域變數。  可惜的是，您無法將 Managed 物件指派給這些類型的變數。  您可以將與 <xref:System.Windows.Interop.HwndSource> 物件相關聯的視窗控制代碼指派給全域或靜態變數，但這樣並不能存取物件本身。  
  
 此問題最簡單的解決方案，就是實作 Managed 類別，其中包含一組靜態欄位來保存您需要存取之任何 Managed 物件的參考。  此範例使用 `WPFPageHost` 類別來保存 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的參考，以及稍後使用者可能變更之一些屬性的起始值。  這定義在標頭中。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageHost](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]  
  
 `GetHwnd` 函式的後半部會將值指派給這些欄位，以供日後使用，而 `myPage` 仍在範圍內。  
  
<a name="communicating_with_the_page"></a>   
### 與 WPF 內容通訊  
 有兩種與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容通訊的類型。  當使用者按一下 \[確定\] 或 \[取消\] 按鈕時，應用程式會收到來自 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的資訊。  應用程式也有 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，可讓使用者變更各種 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容屬性，例如背景色彩或預設字型大小。  
  
 如上所述，當使用者按一下任一按鈕時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容就會引發 `OnButtonClicked` 事件。  應用程式會將處理常式附加至這個事件，以接收這些通知。  如果使用者按一下 \[確定\] 按鈕，處理常式就會從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容取得使用者資訊，並將其顯示在一組靜態控制項中。  
  
 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]  
  
 處理常式會從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容 `MyPageEventArgs` 接收自訂事件引數物件。  如果使用者按一下 \[確定\] 按鈕，物件的 `IsOK` 屬性就會設為`true` 如果使用者按一下 \[取消\] 按鈕，則會設為 `false`。  
  
 如果使用者按一下 \[確定\] 按鈕，處理常式就會從容器類別取得 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的參考。  然後它會收集由相關聯的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容屬性所保存的使用者資訊，並使用靜態控制項，將資訊顯示在父視窗上。  因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容資料是使用 Managed 字串的形式，它必須經過封送處理，以供 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 控制項使用。  如果使用者按一下 \[取消\] 按鈕，處理常式會清除靜態控制項中的資料。  
  
 應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 提供一組選項按鈕，可讓使用者修改 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的背景色彩，以及數個與字型相關的屬性。  下列範例摘錄自應用程式的視窗程序 \(WndProc\) 及其訊息處理作業，該作業在不同的訊息上設定各種屬性，包括背景色彩。  其他皆相似，所以不顯示。  請參閱完整範例，以了解詳細資料和內容。  
  
 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]  
  
 若要設定背景色彩，請從 `WPFPageHost` 取得 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容 \(`hostedPage`\) 的參考，並將背景色彩屬性設為適當的色彩。  此範例使用三種色彩選項：原始色彩、淺綠色或淺橙紅。  原始背景色彩會在 `WPFPageHost` 類別中儲存為靜態欄位。  若要設定其他兩個色彩，您要建立新的 <xref:System.Windows.Media.SolidColorBrush> 物件，並從 <xref:System.Windows.Media.Colors> 物件傳遞靜態色彩值給建構函式。  
  
<a name="implementing_the_wpf_page"></a>   
## 實作 WPF 頁面  
 您不需要實際的實作知識，即可裝載及使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。  如果 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容是封裝在個別的 [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] 中，它可能是以任何 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 語言建置。  以下是範例中所使用之 [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] 實作的簡短逐步解說。  本節包含下列小節。  
  
<a name="autoNestedSectionsOUTLINE2"></a>   
-   [配置](#page_layout)  
  
-   [將資料傳回主視窗](#returning_data_to_window)  
  
-   [設定 WPF 屬性](#set_page_properties)  
  
<a name="page_layout"></a>   
### 配置  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容中的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目包含五個 <xref:System.Windows.Controls.TextBox> 控制項，並具有相關聯的 <xref:System.Windows.Controls.Label> 控制項：名稱、地址、縣 \(市\)、州 \(省\) 和郵遞區號。  另外還有兩個 <xref:System.Windows.Controls.Button> 控制項：\[確定\] 和 \[取消\]。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容會在 `WPFPage` 類別中實作。  配置是以 <xref:System.Windows.Controls.Grid> 配置項目來處理。  類別繼承自 <xref:System.Windows.Controls.Grid>，如此能有效使其成為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容根項目。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容建構函式會採用所需的寬度和高度，並視情況調整 <xref:System.Windows.Controls.Grid> 大小。  然後它會建立一組 <xref:System.Windows.Controls.ColumnDefinition> 和 <xref:System.Windows.Controls.RowDefinition> 物件，將其分別加入 <xref:System.Windows.Controls.Grid> 基底物件 <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> 和 <xref:System.Windows.Controls.Grid.RowDefinitions%2A> 集合中，以定義基本配置。  這會定義一個包含五個資料列和七個資料行的格線，維度則取決於儲存格的內容。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]  
  
 接著，建構函式會將 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目加入 <xref:System.Windows.Controls.Grid> 中。  第一個項目是標題文字，它是位於格線第一個資料列中間的 <xref:System.Windows.Controls.Label> 控制項。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]  
  
 下一個資料列包含名稱 <xref:System.Windows.Controls.Label> 控制項及其相關聯的 <xref:System.Windows.Controls.TextBox> 控制項。  由於每一個標籤\/文字方塊組都是使用相同的程式碼，所以程式碼會放在一個私用方法組中，然後用於所有五個標籤\/文字方塊組。  這些方法會建立適當的控制項，並呼叫 <xref:System.Windows.Controls.Grid> 類別靜態 <xref:System.Windows.Controls.Grid.SetColumn%2A> 和 <xref:System.Windows.Controls.Grid.SetRow%2A> 方法，以將控制項放在適當的儲存格中。  建立控制項之後，此範例會在 <xref:System.Windows.Controls.Grid> 的 <xref:System.Windows.Controls.Panel.Children%2A> 屬性上呼叫 <xref:System.Windows.Controls.UIElementCollection.Add%2A> 方法，以將控制項加入格線中。  用來加入其餘標籤\/文字方塊組的程式碼很類似。  如需詳細資訊，請參閱範例程式碼。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]  
  
 這兩個方法的實作如下所示：  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]  
  
 最後，此範例會加入 \[確定\] 和 \[取消\] 按鈕，並將事件處理常式附加至其 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]  
  
<a name="returning_data_to_window"></a>   
### 將資料傳回主視窗  
 按一下任一按鈕，就會引發其 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。  主視窗只要將處理常式附加至這些事件，就可以直接從 <xref:System.Windows.Controls.TextBox> 控制項取得資料。  此範例使用較不直接的方法。  它會處理 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容中的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click>，然後引發自訂事件 `OnButtonClicked`，以通知 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。  這樣可以讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容先執行一些參數驗證，再通知主機。  處理常式會從 <xref:System.Windows.Controls.TextBox> 控制項取得文字，再將其指派給公用屬性，然後主機再從中擷取資訊。  
  
 WPFPage.h 中的事件宣告：  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]  
  
 WPFPage.cpp 中的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式：  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]  
  
<a name="set_page_properties"></a>   
### 設定 WPF 屬性  
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 主機可讓使用者變更數個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容屬性。  從 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 端來看，這只是變更內容的問題。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容類別中的實作較為複雜一些，因為沒有單一全域屬性來控制所有控制項的字型。  相反地，每個控制項的適當屬性會在屬性的 set 存取子中變更。  下列範例顯示 `DefaultFontFamily` 屬性的程式碼。  設定屬性時會呼叫一個私用方法，它接著會設定各種控制項的 <xref:System.Windows.Controls.Control.FontFamily%2A> 屬性。  
  
 從 WPFPage.h：  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]  
  
 從 WPFPage.cpp：  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]  
  
## 請參閱  
 <xref:System.Windows.Interop.HwndSource>   
 [WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)