---
title: WPF 和 Win32 互通
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: 860e8f11859bfbd85d6a5f0e4420fda3047bb236
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629840"
---
# <a name="wpf-and-win32-interoperation"></a>WPF 和 Win32 互通
本主題概述如何交互操作 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式碼。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。 不過，如果您已長期開發 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 程式碼，則重複使用該程式碼的一部分可能會更有效率。  

<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>WPF 和 Win32 交互操作基本概念  
 針對 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 與 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式碼之間的交互操作，有兩個基本技術。  
  
- 在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。 使用此技術，您可以使用標準 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗和應用程式架構內 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的進階圖形功能。  
  
- 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容中裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗。 使用此技術，您可以在其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的內容中使用現有的自訂 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 控制項，並跨界限傳遞資料。  
  
 本主題會在概念上介紹所有這些技術。 如需在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]裝載的程式碼導向圖例, 請[參閱逐步解說:將 WPF 內容裝載在](walkthrough-hosting-wpf-content-in-win32.md)Win32 中。 如需在中[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]裝載的程式碼導向圖例, 請[參閱逐步解說:在 WPF](walkthrough-hosting-a-win32-control-in-wpf.md)中裝載 Win32 控制項。  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>WPF 交互操作專案  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Api 是受控碼, 但大部分現有[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]的程式都是以C++非受控的方式寫入。  您無法從[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]真正未受管理的程式呼叫 api。 不過, 搭配使用`/clr`選項[!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)]與編譯器, 您就可以建立混合式受控未受管理的程式, 讓您可以順暢地混合受控和未受管理的 API 呼叫。  
  
 一個專案層級的複雜之處在于, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]您無法將C++檔案編譯成專案。  有數個專案部門技術可彌補這一點。  
  
- 建立包含C#所有[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面做為已編譯元件的 DLL, 然後讓C++可執行檔包含該 dll 做為參考。  
  
- 建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容C#的可執行檔, 並讓它參考包含C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]內容的 DLL。  
  
- 使用<xref:System.Windows.Markup.XamlReader.Load%2A>在執行時間[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入任何[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], 而不是編譯。  
  
- 完全不使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , 並在程式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]代碼中撰寫所有的, 從<xref:System.Windows.Application>建立專案樹狀結構。  
  
 請使用最適合您的方法。  
  
> [!NOTE]
>  如果您之前尚未使用C++/cli, 您可能會注意到一些「新」關鍵字, `gcnew`例如`nullptr`和在交互操作程式碼範例中。 這些關鍵字會取代較舊的雙底線語法`__gc`(), 並為中C++的 managed 程式碼提供更自然的語法。  若要深入瞭解/Cli C++管理的功能, 請參閱[執行時間平臺的元件延伸](/cpp/windows/component-extensions-for-runtime-platforms)模組和[Hello C++,/cli](https://go.microsoft.com/fwlink/?LinkId=98739)。  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>WPF 如何使用 Hwnd  
 若要將大部分的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 設為 "HWND interop"，您需要了解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 如何使用 HWND。 針對任何 HWND, 您無法混合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用 DirectX 轉譯或[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]  /  [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)]轉譯來進行轉譯。 這有幾個隱含意義。 主要，若要完全混合使用這些轉譯模型，您必須建立交互操作方案，並使用您選擇使用之每個轉譯模型的指定區段交互操作。 此外，轉譯行為還會建立交互操作方案可完成之作業的「空間」限制。 [技術領域概觀](technology-regions-overview.md)主題會更詳細地說明「空間」概念。  
  
 HWND 最後會支援畫面上的所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]當您建立<xref:System.Windows.Window>時, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]會建立<xref:System.Windows.Interop.HwndSource>最上層的<xref:System.Windows.Window> HWND, 並使用將和其[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容放在 HWND 內。  應用程式中 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的其餘部分會共用該單一 HWND。 例外狀況是功能表、下拉式方塊下拉式清單和其他快顯視窗。 這些項目會建立自己的最上層視窗，這就是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能表為什麼可以通過包含它的視窗 HWND 邊緣。 當您使用<xref:System.Windows.Interop.HwndHost>將 HWND 放在內部[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]會通知如何將新的子 hwnd 相對[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>于 HWND。  
  
 在每個 HWND 之內和之間，相關的 HWND 概念都十分清楚。 [技術領域概觀](technology-regions-overview.md)主題也會討論這點。  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>將 WPF 內容裝載在 Microsoft Win32 視窗中  
 在視窗上裝載的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]索引鍵是<xref:System.Windows.Interop.HwndSource>類別。 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 這個類別會包裝 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容，以將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容併入 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中作為子視窗。 下列方法會將 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 合併在單一應用程式中。  
  
1. 將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容 (內容根項目) 實作為 Managed 類別。 一般而言, 類別繼承自其中一個可包含多個子專案和/或當做根項目 (例如<xref:System.Windows.Controls.DockPanel>或<xref:System.Windows.Controls.Page>) 使用的類別。 在後續步驟中，這個類別指的是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容類別，而且類別的執行個體指的是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容物件。  
  
2. 使用C++/cli 來執行 Windows 應用程式 如果您從現有的非受控C++應用程式開始, 您通常可以藉由變更專案設定以包含`/clr`編譯器旗標 (可能需要支援`/clr`的完整範圍), 讓它呼叫受控碼。本主題未描述編譯。  
  
3. 將執行緒模型設為單一執行緒 Apartment (STA)。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用此執行緒模型。  
  
4. 處理視窗程序中的 WM_CREATE 通知。  
  
5. 在此處理常式 (或處理常式所呼叫的函式) 內，執行下列動作︰  
  
    1. 使用父視窗<xref:System.Windows.Interop.HwndSource> HWND 做為其`parent`參數來建立新的物件。  
  
    2. 建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容類別的執行個體。  
  
    3. 將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content 物件的參考指派<xref:System.Windows.Interop.HwndSource>給物件<xref:System.Windows.Interop.HwndSource.RootVisual%2A>屬性。  
  
    4. <xref:System.Windows.Interop.HwndSource> 物件<xref:System.Windows.Interop.HwndSource.Handle%2A>屬性包含視窗控制碼 (HWND)。 若要取得可用於應用程式 Unmanaged 部分的 HWND，請將 `Handle.ToPointer()` 轉型為 HWND。  
  
6. 實作 Managed 類別，其中包含靜態欄位來保存 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容物件的參考。 這個類別可讓您從程式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]代碼取得內容物件的參考, 但更重要的是, 它會<xref:System.Windows.Interop.HwndSource>防止您不小心地回收垃圾收集。  
  
7. 將處理常式附加到一或多個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容物件事件，以接收 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容物件的通知。  
  
8. 使用儲存在靜態欄位中的參考來設定屬性及呼叫方法等等，以與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容物件通訊。  
  
> [!NOTE]
>  如果您產生不同的組件，然後參考它，則可以針對使用內容類別之預設部分類別的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的步驟一，執行部分或所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容類別定義。 雖然您通常會在<xref:System.Windows.Application>將物件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]編譯成元件的過程中包含物件, 但您最後不會使用<xref:System.Windows.Application>它做為交互操作的一部分, 但您只需要使用一或多個[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]根類別來處理所參考的檔案供應用程式使用, 並參考其部分類別。 此程序的其餘部分基本上與上述類似。  
>   
>  所有這些步驟都會透過逐步[解說:將 WPF 內容裝載在](walkthrough-hosting-wpf-content-in-win32.md)Win32 中。  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>在 WPF 中裝載 Microsoft Win32 視窗  
 在其他[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容中裝載視窗的關鍵是<xref:System.Windows.Interop.HwndHost>類別。 此類別會將視窗包裝在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目中，而此項目可以新增至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目樹狀結構。 <xref:System.Windows.Interop.HwndHost>也支援 Api, 可讓您執行像是主控視窗的處理訊息等工作。 基本程序如下：  
  
1. 建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的項目樹狀結構 (可以透過程式碼或標記)。 在專案樹狀結構中尋找適當且允許的<xref:System.Windows.Interop.HwndHost>點, 可將實作為子項目加入。 在後續步驟中，這個項目稱為保留項目。  
  
2. 衍生自<xref:System.Windows.Interop.HwndHost>以建立[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]保存內容的物件。  
  
3. 在該主機類別中, 覆<xref:System.Windows.Interop.HwndHost>寫<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>方法。 傳回裝載之視窗的 HWND。 您可能想要將實際控制項包裝為所傳回視窗的子視窗；在主視窗中包裝控制項可提供簡單方式，讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容接收來自控制項的通知。 這項技術可協助修正與託管控制項界限的訊息處理相關的一些 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 問題。  
  
4. 覆寫<xref:System.Windows.Interop.HwndHost>方法<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>和<xref:System.Windows.Interop.HwndHost.WndProc%2A>。 這裡的目的是處理裝載之內容的清除和移除參考，特別是您已建立未受管理物件的參考時。  
  
5. 在程式碼後置檔案中，建立控制項裝載類別的執行個體，並將它設定為保留項目的子系。 通常您會使用事件處理常式 (例如<xref:System.Windows.FrameworkElement.Loaded>), 或使用部分類別的函式。 但是，您也可以透過執行階段行為來新增交互操作內容。  
  
6. 處理選取的視窗訊息，例如控制項通知。 有兩種方法。 兩者都提供訊息資料流的相同存取權，因此您的選擇大部分取決於程式設計便利性。  
  
    - 在<xref:System.Windows.Interop.HwndHost> 方法<xref:System.Windows.Interop.HwndHost.WndProc%2A>的覆寫中, 針對所有訊息 (而不只是關閉訊息) 執行訊息處理。  
  
    - 讓主控[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]元素藉由<xref:System.Windows.Interop.HwndHost.MessageHook>處理事件來處理訊息。 針對傳送至裝載視窗之主要視窗程序的每個訊息，都會引發此事件。  
  
    - 您無法使用<xref:System.Windows.Interop.HwndHost.WndProc%2A>從進程外的視窗來處理訊息。  
  
7. 使用平台叫用來呼叫 Unmanaged `SendMessage` 函式，以與裝載的視窗通訊。  
  
 遵循下列步驟會建立可使用滑鼠輸入的應用程式。 您可以藉由執行<xref:System.Windows.Interop.IKeyboardInputSink>介面, 為託管的視窗加入 tab 鍵支援。  
  
 所有這些步驟都會透過逐步[解說:在 WPF](walkthrough-hosting-a-win32-control-in-wpf.md)中裝載 Win32 控制項。  
  
### <a name="hwnds-inside-wpf"></a>WPF 內的 Hwnd  
 您可以把視為<xref:System.Windows.Interop.HwndHost>特殊的控制項。 (技術上<xref:System.Windows.Interop.HwndHost>而言, <xref:System.Windows.FrameworkElement>是<xref:System.Windows.Controls.Control>衍生類別, 而不是衍生類別, 但可視為互通用途的控制項)。將主控內容[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]的基礎本質抽象化, 讓其餘的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容視為另一個類似控制項的物件, 這應該會轉譯和處理輸入。 <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost>通常會如同任何其他[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>行為, 雖然輸出 (繪製和圖形) 和輸入 (滑鼠和鍵盤) 有一些重要的差異, 這是根據基礎 hwnd 可支援的限制而定。  
  
#### <a name="notable-differences-in-output-behavior"></a>輸出行為的顯著差異  
  
- <xref:System.Windows.FrameworkElement>(也就是<xref:System.Windows.Interop.HwndHost>基類) 有相當多的屬性, 表示 UI 的變更。 其中包括之類的屬性<xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, 會將該專案內的元素配置變更為父系。 不過，這些屬性大部分都不會對應至可能的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 對等項目，即使這類對等項目可能存在。 這些屬性的絶大多數和其意義太特定於轉譯技術，以致對應成為實際。 因此, 設定之類<xref:System.Windows.FrameworkElement.FlowDirection%2A> <xref:System.Windows.Interop.HwndHost>的屬性不會有任何作用。  
  
- <xref:System.Windows.Interop.HwndHost>無法旋轉、縮放、扭曲, 或以其他方式受到轉換影響。  
  
- <xref:System.Windows.Interop.HwndHost>不支援<xref:System.Windows.UIElement.Opacity%2A>屬性 (Alpha 混合)。 如果中的<xref:System.Windows.Interop.HwndHost>內容執行<xref:System.Drawing>包含 Alpha 資訊的作業, 這本身就不<xref:System.Windows.Interop.HwndHost>是違規, 但整體只支援不透明度 = 1.0 (100%)。  
  
- <xref:System.Windows.Interop.HwndHost>會出現在相同最上層[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]視窗中的其他專案上方。 不過, 或<xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ContextMenu>產生的功能表是不同的最上層視窗, 因此會使用正確的<xref:System.Windows.Interop.HwndHost>行為。  
  
- <xref:System.Windows.Interop.HwndHost>不尊重其父系<xref:System.Windows.UIElement>的裁剪區域。 如果您嘗試將<xref:System.Windows.Interop.HwndHost>類別放在捲動區域內或<xref:System.Windows.Controls.Canvas>, 這可能會造成問題。  
  
#### <a name="notable-differences-in-input-behavior"></a>輸入行為的顯著差異  
  
- 一般而言, 當輸入裝置的範圍設定于<xref:System.Windows.Interop.HwndHost>託管[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]區域內時, 輸入事件會直接[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]移至。  
  
- 當滑鼠停留在<xref:System.Windows.Interop.HwndHost>上時, 您的應用程式不會收到[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]滑鼠事件, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]而且屬性<xref:System.Windows.UIElement.IsMouseOver%2A>的值會是`false`。  
  
- `false` <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]當具有鍵盤焦點時, 您的應用程式將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]不會接收鍵盤事件, 而且屬性的值會是。 <xref:System.Windows.Interop.HwndHost>  
  
- 當焦點在<xref:System.Windows.Interop.HwndHost>中且變更至內的另一個控制項時, 您的<xref:System.Windows.Interop.HwndHost> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式將不<xref:System.Windows.UIElement.GotFocus>會<xref:System.Windows.UIElement.LostFocus>接收事件或。  
  
- 相關手寫筆屬性和事件是相似的, 而且不會在手寫筆結束<xref:System.Windows.Interop.HwndHost>時報告資訊。  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>定位處理、助憶鍵和加速器  
 和介面可讓您為混合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]應用程式建立順暢的鍵盤體驗: <xref:System.Windows.Interop.IKeyboardInputSite> <xref:System.Windows.Interop.IKeyboardInputSink>  
  
- [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元件之間的定位處理  
  
- 焦點在 Win32 元件內以及在 WPF 元件內時所使用的助憶鍵和加速器。  
  
 和類別都提供的<xref:System.Windows.Interop.IKeyboardInputSink>執行, 但它們可能不會處理您想要用於更先進之案例的所有輸入訊息。 <xref:System.Windows.Interop.HwndSource> <xref:System.Windows.Interop.HwndHost> 覆寫適當的方法，以取得您想要的鍵盤行為。  
  
 這些介面僅支援在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 與 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 區域之間轉換時所發生的情況。 在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 區域內，定位處理行為完全是透過 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 實作的定位處理邏輯所控制 (如果有的話)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [逐步解說：在 WPF 中裝載 Win32 控制項](walkthrough-hosting-a-win32-control-in-wpf.md)
- [逐步解說：將 WPF 內容裝載在 Win32 中](walkthrough-hosting-wpf-content-in-win32.md)
