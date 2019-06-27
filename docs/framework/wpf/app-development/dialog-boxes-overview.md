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
ms.openlocfilehash: 8008feb91a72353a74a647cf79bcecbf7023f962
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410563"
---
# <a name="dialog-boxes-overview"></a>對話方塊概觀
獨立應用程式通常具有主視窗，其中顯示的主要資料的應用程式運作，並公開的功能來處理該資料透過[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]功能表列、 工具列和狀態列等機制。 重要的應用程式還可能顯示其他視窗來執行下列動作：  
  
- 對使用者顯示特定資訊。  
  
- 向使用者收集資訊。  
  
- 顯示並收集資訊。  
  
 這種視窗稱為*對話方塊*，而且有兩種類型： 強制回應和非強制回應。  
  
 A*強制回應*函式需要額外的資料，從繼續使用者時，將會顯示函式的對話方塊。 由於該函式需要透過強制回應對話方塊收集資料，因此當強制回應對話方塊保持開啟時，也可以防止使用者在應用程式中啟動其他視窗。 在大部分情況下，強制回應對話方塊，讓使用者能夠藉由按下 [已完成的強制回應對話方塊時發出信號 **[確定]** 或是**取消**] 按鈕。 按下**確定**按鈕表示使用者已輸入資料，並想要繼續處理該資料的函式。 按下**取消**按鈕表示使用者想要停止完全執行此函式。 強制回應對話方塊的最常見範例為開啟、儲存及列印資料。  
  
 A*非強制回應* 對話方塊中，相反地，不會防止使用者啟動其他視窗開啟時。 例如，如果使用者想要尋找出現在文件中的特定字組，主視窗通常會開啟對話方塊，詢問使用者要尋找哪個字組。 不過，由於尋找字組並不會防止使用者編輯文件，因此對話方塊不需要是強制回應。 非強制回應對話方塊至少會提供**關閉**按鈕以關閉對話方塊，並可能會提供其他按鈕來執行特定函式，例如**尋找下一個**按鈕來尋找下一步，word比對準則的文字搜尋。  
  
 Windows Presentation Foundation (WPF) 可讓您建立數種類型的對話方塊，包括訊息方塊、 通用對話方塊，以及自訂對話方塊。 本主題將討論每個，而[對話方塊範例](https://go.microsoft.com/fwlink/?LinkID=159984)提供相符的範例。  

<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>訊息方塊  
 A*訊息方塊*是可用來顯示文字資訊，並允許使用者透過按鈕做出決定的對話方塊。 下圖所示的訊息方塊顯示文字資訊、提出問題，並提供使用者三個按鈕來回答問題。  
  
 ![文書處理器對話方塊，詢問您是否要將變更儲存至文件的應用程式之前關閉。](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 若要建立訊息方塊，您使用<xref:System.Windows.MessageBox>類別。 <xref:System.Windows.MessageBox> 可讓您設定訊息方塊文字、 標題、 圖示和按鈕，使用如下所示的程式碼。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 若要顯示訊息方塊，請呼叫`static`<xref:System.Windows.MessageBox.Show%2A>方法，如下列程式碼所示。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 當顯示訊息方塊的程式碼必須偵測及處理使用者的決定時 (按下哪個按鈕)，程式碼可以查看訊息方塊結果，如下列程式碼所示。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 如需有關如何使用訊息方塊的詳細資訊，請參閱 < <xref:System.Windows.MessageBox>， [MessageBox 範例](https://go.microsoft.com/fwlink/?LinkID=160023)，以及[對話方塊範例](https://go.microsoft.com/fwlink/?LinkID=159984)。  
  
 雖然<xref:System.Windows.MessageBox>可能會提供簡單的對話方塊方塊中的使用者經驗，使用的優點<xref:System.Windows.MessageBox>就是唯一的可顯示由部分信任安全性沙箱內執行的應用程式的視窗類型 (請參閱[安全性](../security-wpf.md))，例如[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]。  
  
 大多數對話方塊所顯示及收集的資料會比訊息方塊的結果更複雜，包括文字、選取範圍 (核取方塊)、互斥選取範圍 (選項按鈕)，以及清單選取範圍 (清單方塊、下拉式方塊、下拉式清單方塊)。 對於這些 Windows Presentation Foundation (WPF) 提供幾個通用對話方塊，並可讓您建立您自己的對話方塊中，雖然使用任一僅限於以完全信任執行的應用程式。  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>通用對話方塊  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 實作所有應用程式通用之各種可重複使用的對話方塊，包括用於開啟檔案、儲存檔案和列印的對話方塊。 由於這些對話方塊是由作業系統實作，因此可在作業系統上執行的所有應用程式之間共用，以協助確保使用者體驗的一致性；當使用者在一個應用程式中熟悉如何使用某個作業系統提供的對話方塊時，就不需要了解如何在其他應用程式中使用該對話方塊。 因為這些對話方塊分別是提供給所有的應用程式，因為它們可以協助提供一致的使用者體驗，其稱為*通用對話方塊*。  
  
 Windows Presentation Foundation (WPF) 會封裝開啟之檔案、 儲存檔案，並列印通用對話方塊和其公開為 managed 的類別，供您使用獨立應用程式中的資料。 本主題提供每個對話方塊的簡短概觀。  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>開啟檔案 對話方塊  
 如下圖所示，檔案開啟功能使用 [開啟檔案] 對話方塊，來擷取要開啟之檔案的名稱。  
  
 ![開啟的對話方塊中，顯示要擷取檔案的位置。](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 常見的 [開啟檔案] 對話方塊中會實作成<xref:Microsoft.Win32.OpenFileDialog>類別，並位於<xref:Microsoft.Win32>命名空間。 下列程式碼示範如何建立、設定及顯示一個對話方塊，以及如何處理結果。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 如需有關 [開啟檔案] 對話方塊的詳細資訊，請參閱<xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>。  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog> 可以用來安全地擷取檔案名稱，以部分信任執行的應用程式 (請參閱[安全性](../security-wpf.md))。  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>儲存對話方塊  
 如下圖所示，檔案儲存功能使用 [儲存檔案] 對話方塊，來擷取要儲存之檔案的名稱。  
  
 ![另存新檔 對話方塊顯示要儲存檔案的位置。](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 儲存檔案 對話方塊中的一般會實作成<xref:Microsoft.Win32.SaveFileDialog>類別，並位於<xref:Microsoft.Win32>命名空間。 下列程式碼示範如何建立、設定及顯示一個對話方塊，以及如何處理結果。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 如需詳細資訊，另存新檔 對話方塊中，請參閱<xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>。  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>列印對話方塊

如下圖所示，列印功能使用 [列印] 對話方塊，來選擇及設定使用者想要列印資料的目標印表機。  
  
![如果螢幕擷取畫面顯示 [列印] 對話方塊。](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
通用列印對話方塊會實作成<xref:System.Windows.Controls.PrintDialog>類別，並位於<xref:System.Windows.Controls>命名空間。 下列程式碼示範如何建立、設定及顯示一個對話方塊。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 如需有關 [列印] 對話方塊的詳細資訊，請參閱<xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>。 在 WPF 中的列印功能的詳細討論，請參閱[列印概觀](../advanced/printing-overview.md)。  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>自訂對話方塊

雖然通用對話方塊很有用，而且應該盡可能使用，但這類對話方塊並不支援定義域專屬對話方塊的需求。 在此情況下，您必須建立自己的對話方塊。 如稍後所示，對話方塊是具有特殊行為的視窗。 <xref:System.Windows.Window> 實作這些行為，因此，您使用<xref:System.Windows.Window>來建立自訂強制回應和非強制回應對話方塊。  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>建立自訂強制回應對話方塊

本主題說明如何使用<xref:System.Windows.Window>來建立一般強制回應對話方塊方塊實作中，使用`Margins`對話方塊中，做為範例 (請參閱[對話方塊範例](https://go.microsoft.com/fwlink/?LinkID=159984))。 `Margins`下圖顯示對話方塊。  
  
 ![欄位來定義左邊的界、 上方邊界、 右邊界及下邊界的邊界 對話方塊。](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>設定強制回應對話方塊

一般對話方塊的使用者介面包括：  
  
- 收集想要的資料所需的各種控制項。  
  
- **確定**按鈕，使用者按一下以關閉對話方塊，返回函式，並繼續處理。  
  
- A**取消**使用者按一下以關閉對話方塊，然後停止進一步處理的函式的按鈕。  
  
- A**關閉**標題列中的按鈕。  
  
- 圖示。  
  
- **最小化**，**最大化**，以及**還原**按鈕。  
  
- A**系統**功能表以最小化、 最大化、 還原及關閉對話方塊。  
  
- 上方和中央開啟的對話方塊視窗的位置。  
  
- 能夠盡可能以防止對話方塊過小，並為使用者提供實用的預設大小調整大小。 這需要您設定預設值和最小的維度。  
  
- Esc 鍵形式的索引鍵的鍵盤快速鍵**取消**按鈕被按下。 您可以設定<xref:System.Windows.Controls.Button.IsCancel%2A>的屬性**取消**按鈕以`true`。  
  
- ENTER （或 RETURN） 形式的索引鍵的鍵盤快速鍵**確定**按鈕被按下。 您可以設定<xref:System.Windows.Controls.Button.IsDefault%2A>的屬性**確定**  按鈕`true`。  
  
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

在這裡，程式碼會將預設資訊 （目前邊界） 傳遞給對話方塊。 它也會設定<xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType>屬性會顯示對話方塊視窗的參考。 一般情況下，您應該一律設定 對話方塊中的擁有者，以提供視窗狀態相關行為通用於所有對話方塊 (請參閱[WPF Windows 概觀](wpf-windows-overview.md)如需詳細資訊)。

> [!NOTE]
> 您必須提供主控視窗，以支援使用者介面 (UI) 自動化對話方塊 (請參閱[UI 自動化概觀](../../ui-automation/ui-automation-overview.md))。

設定對話方塊之後，它會顯示要強制藉由呼叫<xref:System.Windows.Window.ShowDialog%2A>方法。  
  
#### <a name="validating-user-provided-data"></a>驗證使用者提供的資料

在開啟對話方塊且使用者提供所需資料之後，對話方塊會基於下列原因負責確保提供的資料有效：  
  
- 從安全性的觀點來看，應該驗證所有輸入。  
  
- 從定義域專屬的觀點來看，資料驗證可以防止程式碼處理錯誤的資料，這可能會擲回例外狀況。  
  
- 從使用者體驗的觀點來看，對話方塊可藉由對使用者顯示哪些輸入的資料無效來協助使用者。  
  
- 從效能的觀點來看，多層式應用程式中的資料驗證可以減少用戶層與應用程式層之間的來回行程次數，特別是當應用程式是由 Web 服務或伺服器架構資料庫組成時。  

若要驗證繫結的控制項，在 WPF 中，您需要定義驗證規則，並將它與繫結產生關聯。 驗證規則是自訂的類別衍生自<xref:System.Windows.Controls.ValidationRule>。 下列範例顯示的驗證規則， `MarginValidationRule`，繫結的值是用來檢查<xref:System.Double>，並且在指定的範圍內。  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

在這段程式碼，驗證規則的驗證邏輯會實作藉由覆寫<xref:System.Windows.Controls.ValidationRule.Validate%2A>方法，它會驗證資料，並傳回適當<xref:System.Windows.Controls.ValidationResult>。  

若要建立驗證規則與繫結控制項的關聯，您可以使用下列標記。  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

一旦驗證規則相關聯，WPF 會自動套用其繫結控制項中輸入資料時。 當控制項包含無效的資料時，WPF 會顯示在無效的控制項周圍的紅色框線，如下圖所示。  
  
![無效的左邊的界值周圍的紅色框線的邊界 對話方塊。](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF 不無效的控制來限制使用者，直到使用者輸入有效的資料。 這是很好的對話方塊行為；使用者應該能夠自由地巡覽對話方塊中的控制項，而不論資料是否有效。 不過，這表示使用者可以輸入無效的資料，然後按**確定** 按鈕。 基於這個理由，您的程式碼也需要驗證對話方塊中的所有控制項時 **[確定]** 藉由處理按下按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

此程式碼會列舉視窗上的所有相依性物件，如果有任何無效 (所傳回<xref:System.Windows.Controls.Validation.GetHasError%2A>，在無效的控制項取得焦點，`IsValid`方法會傳回`false`，和視窗會視為無效。  
  
一旦對話方塊有效，就可以安全地將它關閉並傳回。 在傳回過程中，必須將結果傳回呼叫函式。  
  
#### <a name="setting-the-modal-dialog-result"></a>設定強制回應對話方塊結果

開啟對話方塊方塊中，使用<xref:System.Windows.Window.ShowDialog%2A>基本上就像是呼叫方法： 開啟對話方塊方塊中，使用的程式碼<xref:System.Windows.Window.ShowDialog%2A>等到<xref:System.Windows.Window.ShowDialog%2A>傳回。 當<xref:System.Windows.Window.ShowDialog%2A>傳回，程式碼需要呼叫它來決定是否要繼續處理還是停止處理，根據使用者所按下**確定**  按鈕或**取消** 按鈕。 為了簡化這項決定，對話方塊必須傳回做為使用者選擇<xref:System.Boolean>會從傳回的值<xref:System.Windows.Window.ShowDialog%2A>方法。  

當 **[確定]** 按一下按鈕時，<xref:System.Windows.Window.ShowDialog%2A>應該會傳回`true`。 這藉由設定來達成<xref:System.Windows.Window.DialogResult%2A>屬性對話方塊的方塊時 **[確定]** 按一下按鈕時。  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

請注意，設定<xref:System.Windows.Window.DialogResult%2A>屬性也會使視窗自動關閉，而不需要明確呼叫<xref:System.Windows.Window.Close%2A>。  
  
當**取消**按一下按鈕時，<xref:System.Windows.Window.ShowDialog%2A>應該會傳回`false`，也需要設定<xref:System.Windows.Window.DialogResult%2A>屬性。  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

當按鈕的<xref:System.Windows.Controls.Button.IsCancel%2A>屬性設定為`true`且使用者按下其中一個**取消** 按鈕或 ESC 鍵時，<xref:System.Windows.Window.DialogResult%2A>會自動設為`false`。 下列標記有上述的程式碼，而不需要處理相同的效果<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

對話方塊會自動傳回`false`當使用者按下**關閉**按鈕的標題列中，或選擇**關閉**功能表項目從**System**功能表。  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>處理從強制回應對話方塊傳回的資料  

當<xref:System.Windows.Window.DialogResult%2A>設定的對話方塊中，開啟它的函式可以藉由檢查取得對話方塊結果<xref:System.Windows.Window.DialogResult%2A>屬性時<xref:System.Windows.Window.ShowDialog%2A>傳回。  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

如果對話方塊結果為`true`，函式，做為提示來擷取及處理使用者所提供的資料。  
  
> [!NOTE]
> 之後<xref:System.Windows.Window.ShowDialog%2A>已經傳回，無法重新開啟對話方塊。 您必須改為建立新的執行個體。

如果對話方塊結果為`false`，函式應該適當地結束處理。  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>建立自訂非強制回應對話方塊

非強制回應對話方塊 (例如下圖所示的 [尋找] 對話方塊) 與強制回應對話方塊具有相同的基本外觀。  

![如果螢幕擷取畫面顯示 [尋找] 對話方塊。](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

不過，其行為稍有不同，如下列各節中所述。  
  
#### <a name="opening-a-modeless-dialog-box"></a>開啟非強制回應對話方塊

藉由呼叫開啟非強制回應對話方塊<xref:System.Windows.Window.Show%2A>方法。  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  
 
[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

不同於<xref:System.Windows.Window.ShowDialog%2A>，<xref:System.Windows.Window.Show%2A>會立即傳回。 因此，呼叫視窗無法得知非強制回應對話方塊何時關閉，因此不會知道何時要檢查對話方塊結果，或從對話方塊取得資料以進一步處理。 相反地，對話方塊必須建立其他方式，以將資料傳回呼叫視窗進行處理。  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>處理從非強制回應對話方塊傳回的資料  

在此範例中，`FindDialogBox`可能會傳回一或多個找到的主視窗中，根據的文字，而不需要任何特定的頻率所搜尋的結果。 如同強制回應對話方塊，非強制回應對話方塊可以透過屬性傳回結果。 不過，主控對話方塊的視窗必須知道何時要查看這些屬性。 其中一個做法是，讓對話方塊實作每次找到文字時所引發的事件。 `FindDialogBox` 實作`TextFoundEvent`基於此目的，因此首先需要委派。  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

使用`TextFoundEventHandler`委派，請`FindDialogBox`實作`TextFoundEvent`。
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

因此，`Find`可以引發事件時找到搜尋結果。  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

主控視窗接著需要註冊及處理此事件。

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>關閉非強制回應對話方塊

因為<xref:System.Windows.Window.DialogResult%2A>不需要進行設定，可以關閉非強制回應對話方塊，使用系統提供的機制，包括下列：  
  
- 按一下 **關閉**標題列中的按鈕。  
  
- 按下 ALT+F4。  
  
- 選擇**關閉**從**系統**功能表。  
  
或者，您的程式碼可以呼叫<xref:System.Windows.Window.Close%2A>時**關閉**按一下按鈕時。  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>另請參閱

- [快顯功能表概觀](../controls/popup-overview.md)
- [對話方塊範例](https://go.microsoft.com/fwlink/?LinkID=159984)
