---
title: 對話方塊概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- modeless dialog boxes [WPF]
- dialog boxes [WPF]
- message boxes [WPF]
- modal dialog boxes [WPF]
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
ms.openlocfilehash: bf4617d838ba7f02523d7bbdbb57932c033f4a9e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958667"
---
# <a name="dialog-boxes-overview"></a>對話方塊總覽
獨立應用程式通常會有一個主視窗, 它會顯示應用程式運作的主要資料, 並透過[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]功能表列、工具列和狀態列等機制來公開處理該資料的功能。 重要的應用程式還可能顯示其他視窗來執行下列動作：  
  
- 對使用者顯示特定資訊。  
  
- 向使用者收集資訊。  
  
- 顯示並收集資訊。  
  
 這些類型的視窗稱為*對話方塊*, 而且有兩種類型: 強制回應和非強制回應。  
  
 當函式需要使用者的其他資料才能繼續時, 函數會顯示*模式*對話方塊。 由於該函式需要透過強制回應對話方塊收集資料，因此當強制回應對話方塊保持開啟時，也可以防止使用者在應用程式中啟動其他視窗。 在大部分情況下, 強制回應對話方塊可讓使用者在完成強制回應對話方塊時, 按下 **[確定**] 或 [**取消**] 按鈕來發出信號。 按下 [**確定]** 按鈕, 表示使用者已輸入資料, 而且想要讓該函數繼續處理該資料。 按下 [**取消**] 按鈕表示使用者想要完全停止執行函式。 強制回應對話方塊的最常見範例為開啟、儲存及列印資料。  
  
 另一方面, 非*模式*對話方塊則不會防止使用者在開啟其他視窗時加以啟用。 例如，如果使用者想要尋找出現在文件中的特定字組，主視窗通常會開啟對話方塊，詢問使用者要尋找哪個字組。 不過，由於尋找字組並不會防止使用者編輯文件，因此對話方塊不需要是強制回應。 [非模式] 對話方塊至少會提供關閉對話方塊的 [**關閉**] 按鈕, 而且可能會提供其他按鈕來執行特定函式, 例如 **[尋找下一個]** 按鈕, 以尋找符合文字搜尋搜尋準則的下一個單字。  
  
 Windows Presentation Foundation (WPF) 可讓您建立數種類型的對話方塊, 包括訊息方塊、通用對話方塊和自訂對話方塊。 本主題將討論每個, 而[對話方塊範例](https://go.microsoft.com/fwlink/?LinkID=159984)會提供相符的範例。  

<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>訊息方塊  
 *訊息方塊*是可用來顯示文字資訊的對話方塊, 可讓使用者使用按鈕進行決策。 下圖所示的訊息方塊顯示文字資訊、提出問題，並提供使用者三個按鈕來回答問題。  
  
 ![[文字處理器] 對話方塊, 詢問您是否要在應用程式關閉之前, 先儲存檔的變更。](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 若要建立訊息方塊, 請使用<xref:System.Windows.MessageBox>類別。 <xref:System.Windows.MessageBox>可讓您使用如下所示的程式碼, 設定訊息方塊文字、標題、圖示和按鈕。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 若要顯示訊息方塊, 您可以呼叫`static` <xref:System.Windows.MessageBox.Show%2A>方法, 如下列程式碼所示。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 當顯示訊息方塊的程式碼必須偵測及處理使用者的決定時 (按下哪個按鈕)，程式碼可以查看訊息方塊結果，如下列程式碼所示。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 如需使用訊息方塊的詳細資訊, <xref:System.Windows.MessageBox>請參閱、 [MessageBox 範例](https://go.microsoft.com/fwlink/?LinkID=160023)和[對話方塊範例](https://go.microsoft.com/fwlink/?LinkID=159984)。  
  
 雖然<xref:System.Windows.MessageBox>可能提供簡單的對話方塊使用者經驗, 但使用<xref:System.Windows.MessageBox>的優點是, 在部分信任安全性沙箱中執行的應用程式可以顯示唯一的視窗類型 (請參閱[安全性](../security-wpf.md)), 例如[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
 大多數對話方塊所顯示及收集的資料會比訊息方塊的結果更複雜，包括文字、選取範圍 (核取方塊)、互斥選取範圍 (選項按鈕)，以及清單選取範圍 (清單方塊、下拉式方塊、下拉式清單方塊)。 在這些情況下, Windows Presentation Foundation (WPF) 提供數個常見的對話方塊, 並可讓您建立自己的對話方塊, 雖然僅限於以完全信任執行的應用程式。  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>通用對話方塊  
 Windows 會執行各種可重複使用的對話方塊, 通用於所有應用程式, 包括用來開啟檔案、儲存檔案和列印的對話方塊。 由於這些對話方塊是由作業系統實作，因此可在作業系統上執行的所有應用程式之間共用，以協助確保使用者體驗的一致性；當使用者在一個應用程式中熟悉如何使用某個作業系統提供的對話方塊時，就不需要了解如何在其他應用程式中使用該對話方塊。 因為這些對話方塊可供所有應用程式使用, 而且因為它們有助於提供一致的使用者體驗, 所以也稱為*通用對話方塊*。  
  
 Windows Presentation Foundation (WPF) 會封裝開啟的檔案、儲存檔案和列印通用對話方塊, 並將它們公開為受控類別, 供您在獨立應用程式中使用。 本主題提供每個對話方塊的簡短概觀。  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>開啟檔案對話方塊  
 如下圖所示，檔案開啟功能使用 [開啟檔案] 對話方塊，來擷取要開啟之檔案的名稱。  
  
 ![[開啟] 對話方塊, 其中顯示要取出檔案的位置。](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 一般的 [開啟檔案] 對話方塊會實作為<xref:Microsoft.Win32.OpenFileDialog>類別, 並位於<xref:Microsoft.Win32>命名空間中。 下列程式碼示範如何建立、設定及顯示一個對話方塊，以及如何處理結果。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 如需 [開啟檔案] 對話方塊的詳細資訊, <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>請參閱。  
  
> [!NOTE]
> <xref:Microsoft.Win32.OpenFileDialog>可以用來安全地透過以部分信任執行的應用程式來抓取檔案名 (請參閱[安全性](../security-wpf.md))。  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>儲存對話方塊  
 如下圖所示，檔案儲存功能使用 [儲存檔案] 對話方塊，來擷取要儲存之檔案的名稱。  
  
 ![[另存新檔] 對話方塊, 其中顯示儲存檔案的位置。](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 [一般儲存檔案] 對話方塊會實作為<xref:Microsoft.Win32.SaveFileDialog>類別, 並位於<xref:Microsoft.Win32>命名空間中。 下列程式碼示範如何建立、設定及顯示一個對話方塊，以及如何處理結果。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 如需 [儲存檔案] 對話方塊的詳細資訊<xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>, 請參閱。  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>列印對話方塊

如下圖所示，列印功能使用 [列印] 對話方塊，來選擇及設定使用者想要列印資料的目標印表機。  
  
![顯示 [列印] 對話方塊的螢幕擷取畫面。](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
一般 [列印] 對話方塊會實作為<xref:System.Windows.Controls.PrintDialog>類別, 並位於<xref:System.Windows.Controls>命名空間中。 下列程式碼示範如何建立、設定及顯示一個對話方塊。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 如需 [列印] 對話方塊的詳細資訊, <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>請參閱。 如需在 WPF 中列印的詳細討論, 請參閱[列印總覽](../advanced/printing-overview.md)。  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>自訂對話方塊

雖然通用對話方塊很有用，而且應該盡可能使用，但這類對話方塊並不支援定義域專屬對話方塊的需求。 在此情況下，您必須建立自己的對話方塊。 如稍後所示，對話方塊是具有特殊行為的視窗。 <xref:System.Windows.Window>會執行這些行為, 因此, 您可以<xref:System.Windows.Window>使用來建立自訂的強制回應和非強制回應對話方塊。  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>建立模式自訂對話方塊

本主題說明如何使用<xref:System.Windows.Window>來建立典型的強制回應對話方塊實`Margins`作為範例 (請參閱[對話方塊範例](https://go.microsoft.com/fwlink/?LinkID=159984))。 下`Margins`圖顯示此對話方塊。  
  
 ![[邊界] 對話方塊, 其中包含用來定義左邊界、上邊界、右邊界和下邊界的欄位。](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>設定強制回應對話方塊

一般對話方塊的使用者介面包括：  
  
- 收集想要的資料所需的各種控制項。  
  
- 使用者按一下 **[確定**] 按鈕以關閉對話方塊, 並返回函式, 然後繼續處理。  
  
- [**取消**] 按鈕, 使用者可以按一下以關閉對話方塊, 並停止函式進行進一步的處理。  
  
- 標題列中的 [**關閉**] 按鈕。  
  
- 圖示。  
  
- **最小化**、**最大化**和**還原**按鈕。  
  
- 用來最小化、最大化、還原和關閉對話方塊的**系統**功能表。  
  
- 在開啟對話方塊之視窗的上方和中央位置。  
  
- 能夠在可能的情況下調整大小, 讓對話方塊無法變得太小, 並為使用者提供實用的預設大小。 這需要您設定預設值和最小維度。  
  
- ESC 鍵, 做為鍵盤快速鍵, 可讓您按下 [**取消**] 按鈕。 方法是將 [**取消**] <xref:System.Windows.Controls.Button.IsCancel%2A>按鈕的屬性設為`true`。  
  
- 輸入 (或傳回) 鍵做為鍵盤快速鍵, 可讓您按下 [**確定]** 按鈕。 您可以藉由設定<xref:System.Windows.Controls.Button.IsDefault%2A> [**確定]** 按鈕`true`的屬性來執行此動作。  
  
下列程式碼示範這項設定。  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
對話方塊的使用者體驗也會延伸至開啟對話方塊之視窗的功能表列。 當功能表項目所執行的函式需要透過對話方塊進行使用者互動才能繼續時，該函式的功能表項目會在其標頭中顯示省略符號，如下所示。  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
當功能表項目所執行的函式顯示不需要使用者互動的對話方塊時 (例如 [關於] 對話方塊)，則不需要省略符號。  
  
#### <a name="opening-a-modal-dialog-box"></a>開啟強制回應對話方塊

對話方塊通常是使用者選取功能表項目以執行定義域專屬函式所顯示的結果，例如在文書處理器中設定文件的邊界。 將視窗顯示為對話方塊類似於顯示標準視窗，不過需要進行額外的對話方塊專屬設定。 具現化、設定及開啟對話方塊的整個過程如下列程式碼所示。  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

在這裡, 此程式碼會將預設資訊 (目前的邊界) 傳遞至對話方塊。 它也會使用<xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType>顯示對話方塊之視窗的參考來設定屬性。 一般來說, 您應該一律設定對話方塊的 [擁有者], 提供所有對話方塊通用的視窗狀態相關行為 (如需詳細資訊, 請參閱[WPF Windows 總覽](wpf-windows-overview.md))。

> [!NOTE]
> 您必須提供擁有者, 以支援對話方塊的使用者介面 (UI) 自動化 (請參閱[UI 自動化總覽](../../ui-automation/ui-automation-overview.md))。

設定對話方塊之後, 會藉由呼叫<xref:System.Windows.Window.ShowDialog%2A>方法來以模式顯示。  
  
#### <a name="validating-user-provided-data"></a>驗證使用者提供的資料

在開啟對話方塊且使用者提供所需資料之後，對話方塊會基於下列原因負責確保提供的資料有效：  
  
- 從安全性的觀點來看，應該驗證所有輸入。  
  
- 從定義域專屬的觀點來看，資料驗證可以防止程式碼處理錯誤的資料，這可能會擲回例外狀況。  
  
- 從使用者體驗的觀點來看，對話方塊可藉由對使用者顯示哪些輸入的資料無效來協助使用者。  
  
- 從效能的觀點來看，多層式應用程式中的資料驗證可以減少用戶層與應用程式層之間的來回行程次數，特別是當應用程式是由 Web 服務或伺服器架構資料庫組成時。  

若要在 WPF 中驗證繫結控制項, 您必須定義驗證規則, 並將它與系結產生關聯。 驗證規則是衍生<xref:System.Windows.Controls.ValidationRule>自的自訂類別。 下列範例顯示驗證規則, `MarginValidationRule`它<xref:System.Double>會檢查系結的值是否為, 而且是否在指定的範圍內。  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

在此程式碼中, 驗證規則的驗證邏輯是藉由覆寫<xref:System.Windows.Controls.ValidationRule.Validate%2A>方法來執行, 它會驗證資料並傳回<xref:System.Windows.Controls.ValidationResult>適當的。  

若要建立驗證規則與繫結控制項的關聯，您可以使用下列標記。  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

一旦與驗證規則相關聯, WPF 會在將資料輸入繫結控制項時自動套用。 當控制項包含不正確資料時, WPF 會在不正確控制項周圍顯示紅色框線, 如下圖所示。  
  
![邊界對話方塊, 在不正確左邊界值周圍有紅色框線。](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF 在輸入有效的資料之前, 不會將使用者限制為不正確控制項。 這是很好的對話方塊行為；使用者應該能夠自由地巡覽對話方塊中的控制項，而不論資料是否有效。 不過, 這表示使用者可以輸入不正確資料, 然後按下 [**確定]** 按鈕。 基於這個理由, 您的程式碼也需要在處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件時按下 [**確定**] 按鈕時, 驗證對話方塊中的所有控制項。  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

這個程式碼會列舉視窗上的所有相依性物件, 如果有任何不正確 ( <xref:System.Windows.Controls.Validation.GetHasError%2A>如所傳回), 則不正確控制項會`IsValid`取得焦點`false`, 方法會傳回, 而此視窗會被視為無效。  
  
一旦對話方塊有效，就可以安全地將它關閉並傳回。 在傳回過程中，必須將結果傳回呼叫函式。  
  
#### <a name="setting-the-modal-dialog-result"></a>設定強制回應對話方塊結果

使用<xref:System.Windows.Window.ShowDialog%2A>開啟對話方塊, 基本上就像呼叫方法一樣: 使用<xref:System.Windows.Window.ShowDialog%2A>開啟對話方塊的程式碼會等候, 直到傳回<xref:System.Windows.Window.ShowDialog%2A>為止。 當<xref:System.Windows.Window.ShowDialog%2A>傳回時, 呼叫它的程式碼必須根據使用者是否按下 [**確定]** 按鈕或 [**取消**] 按鈕, 決定是否要繼續處理或停止處理。 為了協助進行這<xref:System.Boolean> <xref:System.Windows.Window.ShowDialog%2A>種決策, 對話方塊必須傳回使用者的選擇, 做為從方法傳回的值。  

按一下 [**確定]** 按鈕時, <xref:System.Windows.Window.ShowDialog%2A>應該`true`會傳回。 當按一下 [**確定]** 按鈕<xref:System.Windows.Window.DialogResult%2A>時, 設定對話方塊的屬性即可達成此目的。  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

請注意, 設定<xref:System.Windows.Window.DialogResult%2A>屬性也會使視窗自動關閉, 這可減輕明確呼叫<xref:System.Windows.Window.Close%2A>的需求。  
  
按一下 [**取消**] 按鈕時, <xref:System.Windows.Window.ShowDialog%2A>應該`false`會傳回, 這也需要設定<xref:System.Windows.Window.DialogResult%2A>屬性。  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

當<xref:System.Windows.Controls.Button.IsCancel%2A>按鈕的屬性設定為`true` , 而且使用者按下 [**取消**] 按鈕或 ESC 鍵時, <xref:System.Windows.Window.DialogResult%2A>會自動設定為。 `false` 下列標記與上述程式碼具有相同的效果, 而不需要處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

當使用者按下標題`false`欄中的 [**關閉**] 按鈕, 或從 [**系統**] 功能表選擇 [**關閉**] 功能表項目時, 對話方塊就會自動返回。  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>處理從強制回應對話方塊傳回的資料  

當<xref:System.Windows.Window.DialogResult%2A>由對話方塊設定時, 開啟它的函式可以在傳回時<xref:System.Windows.Window.DialogResult%2A> <xref:System.Windows.Window.ShowDialog%2A>檢查屬性, 以取得對話方塊的結果。  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

如果對話方塊結果為, `true`則函式會使用該函式做為提示, 以取得並處理使用者所提供的資料。  
  
> [!NOTE]
> 傳回<xref:System.Windows.Window.ShowDialog%2A>之後, 就無法重新開啟對話方塊。 您必須改為建立新的執行個體。

如果對話方塊結果為`false`, 函數應該會適當地結束處理。  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>建立非模式自訂對話方塊

非強制回應對話方塊 (例如下圖所示的 [尋找] 對話方塊) 與強制回應對話方塊具有相同的基本外觀。  

![顯示 [尋找] 對話方塊的螢幕擷取畫面。](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

不過，其行為稍有不同，如下列各節中所述。  
  
#### <a name="opening-a-modeless-dialog-box"></a>開啟非強制回應對話方塊

藉由呼叫<xref:System.Windows.Window.Show%2A>方法, 即可開啟非強制回應對話方塊。  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  
 
[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

不同<xref:System.Windows.Window.ShowDialog%2A>于<xref:System.Windows.Window.Show%2A> , 會立即傳回。 因此，呼叫視窗無法得知非強制回應對話方塊何時關閉，因此不會知道何時要檢查對話方塊結果，或從對話方塊取得資料以進一步處理。 相反地，對話方塊必須建立其他方式，以將資料傳回呼叫視窗進行處理。  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>處理從非強制回應對話方塊傳回的資料  

在此範例中, `FindDialogBox`可能會將一或多個尋找結果傳回主視窗, 視搜尋的文字沒有任何特定頻率而定。 如同強制回應對話方塊，非強制回應對話方塊可以透過屬性傳回結果。 不過，主控對話方塊的視窗必須知道何時要查看這些屬性。 其中一個做法是，讓對話方塊實作每次找到文字時所引發的事件。 `FindDialogBox``TextFoundEvent`針對此目的執行, 這會先需要委派。  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

使用委派時`FindDialogBox` ,`TextFoundEvent`會執行。 `TextFoundEventHandler`
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

因此, `Find`可以在找到搜尋結果時引發事件。  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

主控視窗接著需要註冊及處理此事件。

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>關閉非強制回應對話方塊

因為<xref:System.Windows.Window.DialogResult%2A>不需要設定, 所以您可以使用系統提供的機制來關閉非強制回應對話方塊, 包括下列各項:  
  
- 按一下標題列中的 [**關閉**] 按鈕。  
  
- 按下 ALT+F4。  
  
- 從 [**系統**] 功能表選擇 [**關閉**]。  
  
或者, 當您按一下 [ <xref:System.Windows.Window.Close%2A> **關閉**] 按鈕時, 您的程式碼可以呼叫。  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>另請參閱

- [快顯功能表概觀](../controls/popup-overview.md)
- [對話方塊範例](https://go.microsoft.com/fwlink/?LinkID=159984)
