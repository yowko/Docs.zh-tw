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
ms.openlocfilehash: c98d6a45d151d4b683a21e48eaeb5f4a19eaadb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187447"
---
# <a name="dialog-boxes-overview"></a>對話方塊概述
獨立應用程式通常有一個主視窗，該視窗既顯示應用程式運行的主資料，又公開通過[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]功能表列、工具列和狀態列等機制處理該資料的功能。 重要的應用程式還可能顯示其他視窗來執行下列動作：  
  
- 對使用者顯示特定資訊。  
  
- 向使用者收集資訊。  
  
- 顯示並收集資訊。  
  
 這些類型的視窗稱為*對話方塊*，有兩種類型：模式和無模式。  
  
 當函數需要使用者的其他資料以繼續時，函數將顯示*模式*對話方塊。 由於該函式需要透過強制回應對話方塊收集資料，因此當強制回應對話方塊保持開啟時，也可以防止使用者在應用程式中啟動其他視窗。 在大多數情況下，強制回應對話方塊允許使用者在完成強制回應對話方塊後通過按下 **"確定"** 或 **"取消"** 按鈕發出信號。 按下 **"確定"** 按鈕表示使用者已輸入資料，並希望該函數繼續處理該資料。 按下 **"取消"** 按鈕表示使用者希望完全停止該函數的執行。 強制回應對話方塊的最常見範例為開啟、儲存及列印資料。  
  
 另一方面，*無模式*對話方塊不會阻止使用者在打開時啟動其他視窗。 例如，如果使用者想要尋找出現在文件中的特定字組，主視窗通常會開啟對話方塊，詢問使用者要尋找哪個字組。 不過，由於尋找字組並不會防止使用者編輯文件，因此對話方塊不需要是強制回應。 無強制回應對話方塊至少提供關閉對話方塊的 **"關閉"** 按鈕，並可能提供用於執行特定功能的其他按鈕，例如 **"查找下一步**"按鈕，以查找與單詞搜索的查找條件匹配的下一個單詞。  
  
 Windows 演示文稿基礎 （WPF） 允許您創建多種類型的對話方塊，包括訊息方塊、通用對話方塊和自訂對話方塊。 本主題討論每個，[對話方塊示例](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)提供匹配的示例。  

<a name="Message_Boxes"></a>
## <a name="message-boxes"></a>訊息方塊  
 *訊息方塊*是一個對話方塊，可用於顯示文本資訊並允許使用者使用按鈕做出決定。 下圖所示的訊息方塊顯示文字資訊、提出問題，並提供使用者三個按鈕來回答問題。  
  
 ![Word 處理器對話方塊，詢問是否要在應用程式關閉之前保存對文檔的更改。](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 要創建訊息方塊，請使用 類<xref:System.Windows.MessageBox>。 <xref:System.Windows.MessageBox>允許您使用如下所示的代碼配置訊息方塊文本、標題、圖示和按鈕。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 要顯示訊息方塊，請調用`static`<xref:System.Windows.MessageBox.Show%2A>方法，如下代碼所示。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 當顯示訊息方塊的程式碼必須偵測及處理使用者的決定時 (按下哪個按鈕)，程式碼可以查看訊息方塊結果，如下列程式碼所示。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 有關使用訊息方塊的詳細資訊，請參閱<xref:System.Windows.MessageBox>、[訊息方塊示例](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)和[對話方塊示例](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)。  
  
 儘管<xref:System.Windows.MessageBox>可以提供簡單的對話方塊使用者體驗，但使用<xref:System.Windows.MessageBox>的優點是，在部分信任安全沙箱中運行的應用程式可以顯示的唯一視窗類型（請參閱[安全性](../security-wpf.md)），如 XAML 瀏覽器應用程式 （XBAPs）。  
  
 大多數對話方塊所顯示及收集的資料會比訊息方塊的結果更複雜，包括文字、選取範圍 (核取方塊)、互斥選取範圍 (選項按鈕)，以及清單選取範圍 (清單方塊、下拉式方塊、下拉式清單方塊)。 對於這些，Windows 演示文稿基礎 （WPF） 提供了幾個常見的對話方塊，並允許您創建自己的對話方塊，儘管其中任一對話方塊的使用僅限於完全信任運行的應用程式。  
  
<a name="Common_Dialogs"></a>
## <a name="common-dialog-boxes"></a>常見對話方塊  
 Windows 實現所有應用程式共有的各種可重用對話方塊，包括用於打開檔、保存檔和列印的對話方塊。 由於這些對話方塊是由作業系統實作，因此可在作業系統上執行的所有應用程式之間共用，以協助確保使用者體驗的一致性；當使用者在一個應用程式中熟悉如何使用某個作業系統提供的對話方塊時，就不需要了解如何在其他應用程式中使用該對話方塊。 由於這些對話方塊對所有應用程式都可用，並且因為它們有助於提供一致的使用者體驗，因此它們稱為*通用對話方塊*。  
  
 Windows 演示文稿基礎 （WPF） 封裝打開的檔、保存檔並列印公共對話方塊，並將其公開為託管類，供您在獨立應用程式中使用。 本主題提供每個對話方塊的簡短概觀。  
  
<a name="Open_File_Dialog"></a>
### <a name="open-file-dialog"></a>打開檔對話方塊  
 如下圖所示，檔案開啟功能使用 [開啟檔案] 對話方塊，來擷取要開啟之檔案的名稱。  
  
 ![顯示要檢索檔的位置的打開對話方塊。](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 公共打開的檔對話方塊作為類實現，<xref:Microsoft.Win32.OpenFileDialog>位於命名空間中。 <xref:Microsoft.Win32> 下列程式碼示範如何建立、設定及顯示一個對話方塊，以及如何處理結果。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 有關打開的檔對話方塊的詳細資訊，請參閱<xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>。  
  
> [!NOTE]
> <xref:Microsoft.Win32.OpenFileDialog>可用於通過運行具有部分信任的應用程式安全地檢索檔案名（請參閱[安全](../security-wpf.md)）。  
  
<a name="Save_File_Dialog"></a>
### <a name="save-file-dialog-box"></a>儲存對話方塊  
 如下圖所示，檔案儲存功能使用 [儲存檔案] 對話方塊，來擷取要儲存之檔案的名稱。  
  
 ![顯示保存檔的位置的對話方塊。](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 公共保存檔對話方塊作為<xref:Microsoft.Win32.SaveFileDialog>類實現，並位於命名空間中。 <xref:Microsoft.Win32> 下列程式碼示範如何建立、設定及顯示一個對話方塊，以及如何處理結果。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 有關保存檔對話方塊的詳細資訊，請參閱<xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>。  
  
<a name="Print_Dialog"></a>
### <a name="print-dialog-box"></a>列印對話方塊

如下圖所示，列印功能使用 [列印] 對話方塊，來選擇及設定使用者想要列印資料的目標印表機。  
  
![顯示"列印"對話方塊的螢幕截圖。](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
公共列印對話方塊作為<xref:System.Windows.Controls.PrintDialog>類實現，並位於命名空間中。 <xref:System.Windows.Controls> 下列程式碼示範如何建立、設定及顯示一個對話方塊。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 有關列印對話方塊的詳細資訊，請參閱<xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>。 有關 WPF 中列印的詳細討論，請參閱[列印概述](../advanced/printing-overview.md)。  
  
<a name="Custom_Dialog_Boxes"></a>
## <a name="custom-dialog-boxes"></a>自訂對話方塊

雖然通用對話方塊很有用，而且應該盡可能使用，但這類對話方塊並不支援定義域專屬對話方塊的需求。 在此情況下，您必須建立自己的對話方塊。 如稍後所示，對話方塊是具有特殊行為的視窗。 <xref:System.Windows.Window>實現這些行為，因此，您用於<xref:System.Windows.Window>創建自訂模式和無強制回應對話方塊。  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>
### <a name="creating-a-modal-custom-dialog-box"></a>建立模式自訂對話方塊

本主題演示如何使用<xref:System.Windows.Window>`Margins`對話方塊作為示例創建典型的強制回應對話方塊實現（請參閱[對話方塊示例](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)）。 對話方塊`Margins`顯示在下圖中。  
  
 ![帶有用於定義邊距、上邊距、右邊距和下邊距的欄位的邊距對話方塊。](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>配置強制回應對話方塊

一般對話方塊的使用者介面包括：  
  
- 收集想要的資料所需的各種控制項。  
  
- 使用者按一下"**確定"** 按鈕以關閉對話方塊、返回到函數並繼續處理。  
  
- 使用者按一下的 **"取消"** 按鈕以關閉對話方塊並停止該函數的進一步處理。  
  
- 標題列中的 **"關閉**"按鈕。  
  
- 圖示。  
  
- **最小化**、**最大化**和**還原**按鈕。  
  
- 用於**最小化**、最大化、還原和關閉對話方塊的系統功能表。  
  
- 打開對話方塊的視窗上方和中心的位置。  
  
- 盡可能調整大小以防止對話方塊太小，並為使用者提供有用的預設大小。 這要求您同時設置預設值和最小維度。  
  
- ESC 鍵作為鍵盤快速鍵，導致按下 **"取消"** 按鈕。 為此，您可以將<xref:System.Windows.Controls.Button.IsCancel%2A>**"取消"** 按鈕的屬性設置為`true`。  
  
- ENTER（或 RETURN）鍵作為鍵盤快速鍵，用於按下 **"確定"** 按鈕。 為此，您可以設置<xref:System.Windows.Controls.Button.IsDefault%2A>**"確定"** 按鈕`true`的屬性。  
  
下列程式碼示範這項設定。  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
對話方塊的使用者體驗也會延伸至開啟對話方塊之視窗的功能表列。 當功能表項目所執行的函式需要透過對話方塊進行使用者互動才能繼續時，該函式的功能表項目會在其標頭中顯示省略符號，如下所示。  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
當功能表項目所執行的函式顯示不需要使用者互動的對話方塊時 (例如 [關於] 對話方塊)，則不需要省略符號。  
  
#### <a name="opening-a-modal-dialog-box"></a>打開強制回應對話方塊

對話方塊通常是使用者選取功能表項目以執行定義域專屬函式所顯示的結果，例如在文書處理器中設定文件的邊界。 將視窗顯示為對話方塊類似於顯示標準視窗，不過需要進行額外的對話方塊專屬設定。 具現化、設定及開啟對話方塊的整個過程如下列程式碼所示。  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

在這裡，代碼將預設資訊（當前邊距）傳遞給對話方塊。 它還使用對顯示<xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType>對話方塊的視窗的引用設置屬性。 通常，應始終設置對話方塊的擁有者以提供所有對話方塊共有的視窗狀態相關行為（有關詳細資訊，請參閱[WPF Windows 概述](wpf-windows-overview.md)）。

> [!NOTE]
> 您必須提供擁有者以支援對話方塊的使用者介面 （UI） 自動化（請參閱 UI[自動化概述](../../ui-automation/ui-automation-overview.md)）。

配置對話方塊後，通過調用<xref:System.Windows.Window.ShowDialog%2A>方法以模態方式顯示該對話方塊。  
  
#### <a name="validating-user-provided-data"></a>驗證使用者提供的資料

在開啟對話方塊且使用者提供所需資料之後，對話方塊會基於下列原因負責確保提供的資料有效：  
  
- 從安全性的觀點來看，應該驗證所有輸入。  
  
- 從定義域專屬的觀點來看，資料驗證可以防止程式碼處理錯誤的資料，這可能會擲回例外狀況。  
  
- 從使用者體驗的觀點來看，對話方塊可藉由對使用者顯示哪些輸入的資料無效來協助使用者。  
  
- 從效能的觀點來看，多層式應用程式中的資料驗證可以減少用戶層與應用程式層之間的來回行程次數，特別是當應用程式是由 Web 服務或伺服器架構資料庫組成時。  

要驗證 WPF 中的繫結控制項，需要定義驗證規則並將其與綁定相關聯。 驗證規則是從 派生的自訂類<xref:System.Windows.Controls.ValidationRule>。 下面的示例顯示驗證規則，`MarginValidationRule`該規則檢查綁定值是否為 和<xref:System.Double>，並且在指定範圍內。  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

在此代碼中，驗證規則的驗證邏輯是通過重寫<xref:System.Windows.Controls.ValidationRule.Validate%2A>方法實現的，該方法驗證資料並返回適當的<xref:System.Windows.Controls.ValidationResult>。  

若要建立驗證規則與繫結控制項的關聯，您可以使用下列標記。  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

關聯驗證規則後，WPF 將自動在將資料輸入繫結控制項時應用它。 當控制項包含無效資料時，WPF 將在無效控制項周圍顯示紅色邊框，如下圖所示。  
  
![邊距對話方塊，其紅色邊框圍繞不正確左邊距值。](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF 不會將使用者限制為無效控制項，直到使用者輸入有效資料。 這是很好的對話方塊行為；使用者應該能夠自由地巡覽對話方塊中的控制項，而不論資料是否有效。 但是，這意味著使用者可以輸入無效資料並按下 **"確定"** 按鈕。 因此，當通過處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件按下 **"確定"** 按鈕時，代碼還需要驗證對話方塊中的所有控制項。  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

此代碼枚舉視窗上的所有依賴項物件，如果任何依賴項物件無效（如<xref:System.Windows.Controls.Validation.GetHasError%2A>返回，無效控制項獲取焦點，`IsValid`則該方法返回`false`，並且視窗被視為無效。  
  
一旦對話方塊有效，就可以安全地將它關閉並傳回。 在傳回過程中，必須將結果傳回呼叫函式。  
  
#### <a name="setting-the-modal-dialog-result"></a>設置模態對話方塊結果

使用<xref:System.Windows.Window.ShowDialog%2A>打開對話方塊從根本上說就像調用方法：使用<xref:System.Windows.Window.ShowDialog%2A>等待直到<xref:System.Windows.Window.ShowDialog%2A>返回打開對話方塊的代碼。 返回<xref:System.Windows.Window.ShowDialog%2A>時，調用它的代碼需要根據使用者是按下 **"確定"** 按鈕還是 **"取消"** 按鈕來決定是繼續處理還是停止處理。 為了便於做出此決策，該對話方塊需要將使用者的選擇作為從<xref:System.Boolean><xref:System.Windows.Window.ShowDialog%2A>方法返回的值返回。  

按一下 **"確定"** 按鈕時，<xref:System.Windows.Window.ShowDialog%2A>應返回`true`。 這是通過在按一下<xref:System.Windows.Window.DialogResult%2A>**"確定"** 按鈕時設置對話方塊的屬性來實現的。  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

請注意，設置<xref:System.Windows.Window.DialogResult%2A>屬性還會導致視窗自動關閉，這減輕了顯式調用<xref:System.Windows.Window.Close%2A>的需要。  
  
按一下 **"取消"** 按鈕時，<xref:System.Windows.Window.ShowDialog%2A>應返回`false`，這還需要設置<xref:System.Windows.Window.DialogResult%2A>屬性。  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

當按鈕的屬性<xref:System.Windows.Controls.Button.IsCancel%2A>設置為`true`，並且使用者按下 **"取消"** 按鈕或 ESC 鍵時，<xref:System.Windows.Window.DialogResult%2A>將自動設置為`false`。 以下標記的效果與前面的代碼相同，無需處理事件<xref:System.Windows.Controls.Primitives.ButtonBase.Click>。  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

當使用者按下標題列中的`false`**"關閉"** 按鈕或從 **"系統**"功能表中選擇"**關閉**"功能表項目時，將自動返回一個對話方塊。  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>處理從強制回應對話方塊返回的資料  

當<xref:System.Windows.Window.DialogResult%2A>由對話方塊設置時，打開它的函數可以通過在返回時<xref:System.Windows.Window.DialogResult%2A><xref:System.Windows.Window.ShowDialog%2A>檢查該屬性來獲取對話方塊的結果。  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

如果對話方塊結果是`true`，則函數將該結果用作檢索和處理使用者提供的資料的提示。  
  
> [!NOTE]
> 返回<xref:System.Windows.Window.ShowDialog%2A>後，無法重新打開對話方塊。 您必須改為建立新的執行個體。

如果對話方塊結果是`false`，則函數應適當地結束處理。  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>
### <a name="creating-a-modeless-custom-dialog-box"></a>創建無模式自訂對話方塊

非強制回應對話方塊 (例如下圖所示的 [尋找] 對話方塊) 與強制回應對話方塊具有相同的基本外觀。  

![顯示"查找"對話方塊的螢幕截圖。](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

不過，其行為稍有不同，如下列各節中所述。  
  
#### <a name="opening-a-modeless-dialog-box"></a>打開無強制回應對話方塊

通過調用<xref:System.Windows.Window.Show%2A>方法打開無強制回應對話方塊。  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  

[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

不像<xref:System.Windows.Window.ShowDialog%2A> <xref:System.Windows.Window.Show%2A> ，立即返回。 因此，呼叫視窗無法得知非強制回應對話方塊何時關閉，因此不會知道何時要檢查對話方塊結果，或從對話方塊取得資料以進一步處理。 相反地，對話方塊必須建立其他方式，以將資料傳回呼叫視窗進行處理。  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>處理從無強制回應對話方塊返回的資料  

在此示例中，`FindDialogBox`可能會將一個或多個查找結果返回給主視窗，具體取決於搜索的文本，而不帶任何特定頻率。 如同強制回應對話方塊，非強制回應對話方塊可以透過屬性傳回結果。 不過，主控對話方塊的視窗必須知道何時要查看這些屬性。 其中一個做法是，讓對話方塊實作每次找到文字時所引發的事件。 `FindDialogBox`實現`TextFoundEvent`為此目的，首先需要委託。  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

使用`TextFoundEventHandler`委託實現`FindDialogBox`。 `TextFoundEvent`
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

因此，`Find`當找到搜尋結果時，可以引發事件。  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

主控視窗接著需要註冊及處理此事件。

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>關閉無強制回應對話方塊

由於<xref:System.Windows.Window.DialogResult%2A>不需要設置，因此可以使用系統提供機制關閉無強制回應對話方塊，包括：  
  
- 按一下標題列中的 **"關閉**"按鈕。  
  
- 按下 ALT+F4。  
  
- 從 **"系統**"功能表中選擇 **"關閉**"。  
  
或者，當按一下"<xref:System.Windows.Window.Close%2A>**關閉**"按鈕時，代碼可以調用。  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>另請參閱

- [快顯功能表概觀](../controls/popup-overview.md)
- [Dialog Box Sample (對話方塊範例)](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)
