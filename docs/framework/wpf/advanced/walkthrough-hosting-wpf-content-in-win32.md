---
title: Win32 中的主機 WPF 內容
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 8a5d556abf49c9c1f49e7853e752ebc5248d1101
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186074"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>逐步解說：在 Win32 中裝載 WPF 內容
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。 但是，當您對 Win32 代碼進行大量投資時，向應用程式添加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]功能而不是重寫原始代碼可能更有效。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供了在 Win32[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]視窗中託管內容的簡單機制。  
  
 本教程介紹如何編寫應用程式範例，[在 Win32 視窗示例中託管 WPF 內容](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage)，該示例[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]在 Win32 視窗中託管內容。 您可以擴展此示例以承載任何 Win32 視窗。 因為它涉及混合託管和非託管代碼，所以應用程式以C++/CLI編寫。  

<a name="requirements"></a>
## <a name="requirements"></a>需求  
 本教程假定對 Win32[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程式設計和 Win32 程式設計基本熟悉。 有關[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程式設計的基本介紹，請參閱[入門](../getting-started/index.md)。 有關 Win32 程式設計的介紹，您應該參考有關該主題的眾多書籍，特別是查理斯·佩佐德的*程式設計 Windows。*  
  
 由於本教程附帶的示例在 C++/CLI 中實現，本教程假定熟悉使用 C++對 Windows API 進行程式設計，並瞭解託管代碼程式設計。 熟悉C++/CLI是有説明的，但不是必須的。  
  
> [!NOTE]
> 本教學課程包含一些來自相關範例的程式碼範例。 不過，為了方便閱讀，並未包含完整的範例程式碼。 有關完整的示例代碼，請參閱[在 Win32 視窗示例中託管 WPF 內容](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage)。  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>基本程序  
 本節概述了用於在 Win32 視窗中託管[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容的基本過程。 其餘各節將說明每個步驟的詳細資訊。  
  
 在 Win32 視窗中託管[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容的關鍵是<xref:System.Windows.Interop.HwndSource>類。 此類將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容包裝在 Win32 視窗中，允許將其作為子視窗合併到您的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]視窗中。 以下方法將 Win32 和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]單個應用程式相結合。  
  
1. 將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容作為託管類實現。  
  
2. 使用C++/CLI實現 Windows 應用程式。 如果要從現有應用程式和非託管C++代碼開始，通常可以通過更改專案設置來包括`/clr`編譯器標誌來啟用它調用託管代碼。  
  
3. 將執行緒模型設為單一執行緒 Apartment (STA)。  
  
4. 在視窗過程中處理[WM_CREATE](/windows/desktop/winmsg/wm-create)通知，並執行以下操作：  
  
    1. 以父視窗做為 <xref:System.Windows.Interop.HwndSource> 參數，建立新的 `parent` 物件。  
  
    2. 建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容類別的執行個體。  
  
    3. 將對[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容物件的引用分配給<xref:System.Windows.Interop.HwndSource.RootVisual%2A>的屬性。 <xref:System.Windows.Interop.HwndSource>  
  
    4. 取得內容的 HWND。 <xref:System.Windows.Interop.HwndSource.Handle%2A> 物件的 <xref:System.Windows.Interop.HwndSource> 屬性包含視窗控制代碼 (HWND)。 若要取得可用於應用程式 Unmanaged 部分的 HWND，請將 `Handle.ToPointer()` 轉型為 HWND。  
  
5. 實作 Managed 類別，其中包含靜態欄位來保存 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的參考。 此類允許您從 Win32 代碼中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]獲取對內容的引用。  
  
6. 將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容指派至靜態欄位。  
  
7. 通過將處理常式附加到一[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]個或多個[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]事件來接收來自內容的通知。  
  
8. 使用儲存在靜態欄位中的參考來設定屬性等等，以與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容通訊。  
  
> [!NOTE]
> 您還可以使用 來實現[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]內容[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 但是，您必須將其單獨編譯為動態連結程式庫 （DLL） 並從 Win32 應用程式中引用該 DLL。 此程序的其餘部分與上述類似。

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>實作主應用程式
 本節介紹如何在基本的 Win32 應用程式中託管[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容。 內容本身在C++/CLI 中作為託管類實現。 大部分的情況下，這就是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式設計。 [在實施WPF內容](#implementing_the_wpf_page)時討論了內容實現的關鍵方面。

- [基本應用程式](#the_basic_application)

- [裝載 WPF 內容](#hosting_the_wpf_page)

- [保存 WPF 內容的參考](#holding_a_reference)

- [與 WPF 內容通訊](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>基本應用程式
 主機應用程式的出發點是創建 Visual Studio 2005 範本。

1. 打開 Visual Studio 2005，並從 **"檔**"功能表中選擇 **"新專案**"。

2. 從視覺化C++專案類型清單中選擇**Win32。** 如果您的預設語言不C++，您將在 **"其他語言"** 下找到這些專案類型。

3. 選擇**Win32 專案**範本，為專案指定名稱，然後按一下 **"確定"** 以啟動**Win32 應用程式精靈**。

4. 接受嚮導的預設設置，然後按一下 **"完成"** 以啟動專案。

 該範本創建基本 Win32 應用程式，包括：

- 應用程式的進入點。

- 視窗，具有相關聯的視窗程序 (WndProc)。

- 包含 **"檔**"和"**説明**"標題的功能表。 "**檔**"功能表具有關閉應用程式的**退出**項。 "**説明"** 功能表具有啟動簡單對話方塊**的"關於**"項。

 在開始編寫代碼以承載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容之前，需要對基本範本進行兩項修改。

 第一個是將專案編譯成 Managed 程式碼。 根據預設，專案會編譯成 Unmanaged 程式碼。 不過，因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是以 Managed 程式碼實作，所以專案必須據以編譯。

1. 按右鍵**解決方案資源管理器**中的專案名稱，並從內容功能表中選擇 **"屬性**"以啟動 **"屬性頁"** 對話方塊。

2. 從左側窗格中的樹狀檢視中選擇 **"配置屬性**"。

3. 從右側窗格中的 **"專案預設值"** 清單中選擇 **"通用語言運行時**支援"。

4. 從下拉式清單方塊中選擇**通用語言運行時支援 （/clr）。**

> [!NOTE]
> 此編譯器旗標可讓您在應用程式中使用 Managed 程式碼，但 Unmanaged 程式碼還是會編譯成和之前一樣。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用單一執行緒 Apartment (STA) 執行緒模型。 為了正確處理[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容代碼，必須通過將屬性應用於進入點，將應用程式的執行緒模型設置為 STA。

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>裝載 WPF 內容
 內容是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]一個簡單的位址輸入應用程式。 它包含數個 <xref:System.Windows.Controls.TextBox> 控制項，以取得使用者名稱、位址等等。 還有兩個<xref:System.Windows.Controls.Button>控制項，**確定**和**取消**。 當使用者按一下 **"確定"** 時，按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>的事件處理常式會從<xref:System.Windows.Controls.TextBox>控制項收集資料，將其分配給相應的屬性，並引發自訂事件 。 `OnButtonClicked` 當使用者按一下 **"取消"** 時，處理常式將僅引發`OnButtonClicked`。 `OnButtonClicked` 的事件引數物件包含布林值的欄位，指出所點選的按鈕。

 承載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容的代碼在主機視窗中[WM_CREATE](/windows/desktop/winmsg/wm-create)通知的處理常式中實現。

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 該方法`GetHwnd`採用大小和位置資訊加上父視窗控制碼，並返回託管[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容的視窗控制碼。

> [!NOTE]
> 您不能將 `#using` 指示詞用於 `System::Windows::Interop` 命名空間。 這麼做會在該命名空間中的 <xref:System.Windows.Interop.MSG> 結構與 winuser.h 中宣告的 MSG 結構之間，造成名稱衝突。 您必須改用完整的名稱來存取該命名空間的內容。

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 您不能直接在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式視窗中託管內容。 相反地，您要先建立 <xref:System.Windows.Interop.HwndSource> 物件來包裝 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。 此物件基本上是一個旨在承載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容的視窗。 通過將<xref:System.Windows.Interop.HwndSource>物件創建為作為應用程式的一部分的 Win32 視窗的子視窗，在父視窗中託管該物件。 <xref:System.Windows.Interop.HwndSource>建構函式參數包含與創建 Win32 子視窗時傳遞給 CreateWindow 的資訊大致相同。

 接下來創建[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容物件的實例。 在這種情況下，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容作為單獨的類實現，`WPFPage`使用C++/CLI。 您也可以使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 來實作 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 內容。 但是，要執行此操作，您需要設置一個單獨的專案，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]並將內容構建為 DLL。 您可以將對該 DLL 的引用添加到專案中，並使用該引用創建內容的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]實例。

 通過將對[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容<xref:System.Windows.Interop.HwndSource.RootVisual%2A>的引用分配給 的屬性<xref:System.Windows.Interop.HwndSource>，在子視窗中顯示內容。

 下一行程式碼會將事件處理常式 `WPFButtonClicked` 附加至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容 `OnButtonClicked` 事件。 當使用者按一下 **"確定"** 或 **"取消"** 按鈕時，將調用此處理程式。 有關此事件處理常式的進一步討論[，請參閱communicating_with_the_WPF內容](#communicating_with_the_page)。

 所顯示的最後一行程式碼會傳回與 <xref:System.Windows.Interop.HwndSource> 物件相關聯的視窗控制代碼 (HWND)。 您可以使用 Win32 代碼中的此控制碼將消息發送到託管視窗，儘管示例不這樣做。 <xref:System.Windows.Interop.HwndSource> 物件每次收到訊息時，都會引發事件。 若要處理這些訊息，請呼叫 <xref:System.Windows.Interop.HwndSource.AddHook%2A> 方法來附加訊息處理常式，然後在該處理常式中處理訊息。

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>保存 WPF 內容的參考
 就許多應用程式而言，您稍後會想要與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容通訊。 例如，您可能會想要修改 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容屬性，或是讓 <xref:System.Windows.Interop.HwndSource> 物件裝載不同的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。 若要這麼做，您需要 <xref:System.Windows.Interop.HwndSource> 物件或 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的參考。 <xref:System.Windows.Interop.HwndSource> 物件及其相關聯的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容會保留在記憶體中，直到您終結視窗控制代碼。 不過，一旦您從視窗程序返回，您指派給 <xref:System.Windows.Interop.HwndSource> 物件的變數就會超出範圍。 使用 Win32 應用程式處理此問題的慣常方法是使用靜態變數或全域變數。 可惜的是，您無法將 Managed 物件指派給這些類型的變數。 您可以將與 <xref:System.Windows.Interop.HwndSource> 物件相關聯的視窗控制代碼指派給全域或靜態變數，但這樣並不能存取物件本身。

 此問題最簡單的解決方案，就是實作 Managed 類別，其中包含一組靜態欄位來保存您需要存取之任何 Managed 物件的參考。 此範例使用 `WPFPageHost` 類別來保存 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的參考，以及稍後使用者可能變更之一些屬性的起始值。 這定義在標頭中。

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 `GetHwnd` 函式的後半部會將值指派給這些欄位，以供日後使用，而 `myPage` 仍在範圍內。

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>與 WPF 內容通訊
 有兩種與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容通訊的類型。 當使用者按一下[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]**"確定"** 或 **"取消"** 按鈕時，應用程式將從內容接收資訊。 應用程式也有 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，可讓使用者變更各種 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容屬性，例如背景色彩或預設字型大小。

 如上所述，當使用者按一下任一按鈕時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容就會引發 `OnButtonClicked` 事件。 應用程式會將處理常式附加至這個事件，以接收這些通知。 如果按一下了 **"確定"** 按鈕，處理常式將從[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容中獲取使用者資訊，並將其顯示在一組靜態控制項中。

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 處理常式會從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容 `MyPageEventArgs` 接收自訂事件引數物件。 `true`如果按一下了 **"確定"** 按鈕，並且`false`按一下了 **"取消"** 按鈕，則物件的屬性`IsOK`將設置為"取消" 按鈕。

 如果按一下了 **"確定"** 按鈕，處理常式將從容器類中獲取對[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容的引用。 然後它會收集由相關聯的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容屬性所保存的使用者資訊，並使用靜態控制項，將資訊顯示在父視窗上。 由於[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容資料以託管字串的形式出現，因此必須將其封送供 Win32 控制項使用。 如果按一下"**取消"** 按鈕，處理常式將清除靜態控制項中的資料。

 應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 提供一組選項按鈕，可讓使用者修改 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的背景色彩，以及數個與字型相關的屬性。 下列範例摘錄自應用程式的視窗程序 (WndProc) 及其訊息處理作業，該作業在不同的訊息上設定各種屬性，包括背景色彩。 其他皆相似，所以不顯示。 請參閱完整範例，以了解詳細資料和內容。

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 若要設定背景色彩，請從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 取得 `hostedPage` 內容 (`WPFPageHost`) 的參考，並將背景色彩屬性設為適當的色彩。 此範例使用三種色彩選項：原始色彩、淺綠色或淺橙紅。 原始背景色彩會在 `WPFPageHost` 類別中儲存為靜態欄位。 若要設定其他兩個色彩，您要建立新的 <xref:System.Windows.Media.SolidColorBrush> 物件，並從 <xref:System.Windows.Media.Colors> 物件傳遞靜態色彩值給建構函式。

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>實作 WPF 頁面
 您可以託管和使用內容，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]而不了解實際實現。 如果[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容已打包在單獨的 DLL 中，則內容可以以任何通用語言運行時 （CLR） 語言構建。 以下是示例中使用的C++/CLI 實現的簡短演練。 本節包含下列小節。

- [版面配置](#page_layout)

- [將資料傳回主視窗](#returning_data_to_window)

- [設定 WPF 屬性](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>版面配置
 內容中[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]的元素由五個<xref:System.Windows.Controls.TextBox>控制群組成，並具有關聯的<xref:System.Windows.Controls.Label>控制項：名稱、位址、城市、州和 Zip。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 還有兩個<xref:System.Windows.Controls.Button>控制項，**確定**和**取消**

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容會在 `WPFPage` 類別中實作。 配置是以 <xref:System.Windows.Controls.Grid> 配置項目來處理。 類別繼承自 <xref:System.Windows.Controls.Grid>，如此能有效使其成為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容根項目。

 內容[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]建構函式採用所需的寬度和高度，並<xref:System.Windows.Controls.Grid>相應地調整大小。 然後<xref:System.Windows.Controls.ColumnDefinition>，它通過創建一組 和<xref:System.Windows.Controls.RowDefinition>物件並分別將它們添加到<xref:System.Windows.Controls.Grid>物件程式庫<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>和<xref:System.Windows.Controls.Grid.RowDefinitions%2A>集合來定義基本佈局。 這會定義一個包含五個資料列和七個資料行的格線，維度則取決於儲存格的內容。

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 接著，建構函式會將 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目加入 <xref:System.Windows.Controls.Grid> 中。 第一個項目是標題文字，它是位於格線第一個資料列中間的 <xref:System.Windows.Controls.Label> 控制項。

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 下一個資料列包含名稱 <xref:System.Windows.Controls.Label> 控制項及其相關聯的 <xref:System.Windows.Controls.TextBox> 控制項。 由於每一個標籤/文字方塊組都是使用相同的程式碼，所以程式碼會放在一個私用方法組中，然後用於所有五個標籤/文字方塊組。 這些方法會建立適當的控制項，並呼叫 <xref:System.Windows.Controls.Grid> 類別靜態 <xref:System.Windows.Controls.Grid.SetColumn%2A> 和 <xref:System.Windows.Controls.Grid.SetRow%2A> 方法，以將控制項放在適當的儲存格中。 建立控制項之後，此範例會在 <xref:System.Windows.Controls.UIElementCollection.Add%2A> 的 <xref:System.Windows.Controls.Panel.Children%2A> 屬性上呼叫 <xref:System.Windows.Controls.Grid> 方法，以將控制項加入格線中。 用來加入其餘標籤/文字方塊組的程式碼很類似。 如需詳細資訊，請參閱範例程式碼。

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 這兩個方法的實作如下所示：

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 最後，該示例添加 **"確定****"和"取消"** 按鈕，並將事件處理常式附加到<xref:System.Windows.Controls.Primitives.ButtonBase.Click>其事件。

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>將資料傳回主視窗
 按一下任一按鈕，就會引發其 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。 主視窗只要將處理常式附加至這些事件，就可以直接從 <xref:System.Windows.Controls.TextBox> 控制項取得資料。 此範例使用較不直接的方法。 它處理內容<xref:System.Windows.Controls.Primitives.ButtonBase.Click>內的內容[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，然後引發自訂事件`OnButtonClicked`，以通知[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容。 這允許內容在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]通知主機之前執行一些參數驗證。 處理常式會從 <xref:System.Windows.Controls.TextBox> 控制項取得文字，再將其指派給公用屬性，然後主機再從中擷取資訊。

 WPFPage.h 中的事件宣告：

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 WPFPage.cpp 中的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式：

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>設定 WPF 屬性
 Win32 主機允許使用者更改多個[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容屬性。 從 Win32 方面來說，這只是更改屬性的問題。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容類別中的實作較為複雜一些，因為沒有單一全域屬性來控制所有控制項的字型。 相反地，每個控制項的適當屬性會在屬性的 set 存取子中變更。 下面的示例顯示了屬性的代碼`DefaultFontFamily`。 設定屬性時會呼叫一個私用方法，它接著會設定各種控制項的 <xref:System.Windows.Controls.Control.FontFamily%2A> 屬性。

 從 WPFPage.h：

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 從 WPFPage.cpp：

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.HwndSource>
- [WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)
