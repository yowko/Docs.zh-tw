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
ms.openlocfilehash: 110e42fea8d5586e471ae36ead46bed304cf9f48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549152"
---
# <a name="dialog-boxes-overview"></a>對話方塊概觀
獨立應用程式通常具有主視窗，同時會顯示主要資料的應用程式運作，並公開的功能來處理該資料透過[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]機制類似功能表列、 工具列和狀態列。 重要的應用程式還可能顯示其他視窗來執行下列動作：  
  
-   對使用者顯示特定資訊。  
  
-   向使用者收集資訊。  
  
-   顯示並收集資訊。  
  
 這些類型的視窗稱為*對話方塊*，而且有兩種類型： 強制回應和非強制回應。  
  
 A*強制回應*函式需要使用者繼續從其他資料時，對話方塊會顯示函式。 由於該函式需要透過強制回應對話方塊收集資料，因此當強制回應對話方塊保持開啟時，也可以防止使用者在應用程式中啟動其他視窗。 在大部分情況下，強制回應對話方塊可讓使用者藉由按下 [已完成的強制回應對話方塊時發出通知**確定**或**取消**] 按鈕。 按下**確定**按鈕表示使用者已輸入的資料，而且想要繼續處理該資料的函式。 按下**取消**按鈕表示使用者想要停止執行的函式。 強制回應對話方塊的最常見範例為開啟、儲存及列印資料。  
  
 A*非強制回應*對話方塊中，相反地，不會防止使用者啟動其他視窗開啟時。 例如，如果使用者想要尋找出現在文件中的特定字組，主視窗通常會開啟對話方塊，詢問使用者要尋找哪個字組。 不過，由於尋找字組並不會防止使用者編輯文件，因此對話方塊不需要是強制回應。 非強制回應對話方塊至少提供**關閉**按鈕來關閉對話方塊，並可能會提供其他按鈕來執行特定的功能，例如**找下一個**按鈕來尋找下一個的比對文字搜尋的尋找的準則。  
  
 Windows Presentation Foundation (WPF) 可讓您建立數種類型的對話方塊中，包括訊息方塊中，通用對話方塊和自訂對話方塊。 本主題將討論每個，而[對話方塊範例](http://go.microsoft.com/fwlink/?LinkID=159984)提供相符的範例。  
  
 
  
<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>訊息方塊  
 A*訊息方塊*是可用來顯示文字資訊，並允許使用者使用按鈕進行決策的對話方塊。 下圖所示的訊息方塊顯示文字資訊、提出問題，並提供使用者三個按鈕來回答問題。  
  
 ![文書處理器對話方塊](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure1.png "DialogBoxesOverviewFigure1")  
  
 若要建立訊息方塊，您使用<xref:System.Windows.MessageBox>類別。 <xref:System.Windows.MessageBox> 可讓您設定訊息方塊文字、 標題、 圖示和按鈕，使用下列程式碼。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 若要顯示的訊息方塊，請呼叫`static`<xref:System.Windows.MessageBox.Show%2A>方法，如下列程式碼所示。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 當顯示訊息方塊的程式碼必須偵測及處理使用者的決定時 (按下哪個按鈕)，程式碼可以查看訊息方塊結果，如下列程式碼所示。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 如需有關如何使用訊息方塊的詳細資訊，請參閱<xref:System.Windows.MessageBox>， [MessageBox 範例](http://go.microsoft.com/fwlink/?LinkID=160023)，和[對話方塊範例](http://go.microsoft.com/fwlink/?LinkID=159984)。  
  
 雖然<xref:System.Windows.MessageBox>可能提供較簡單的對話方塊方塊使用者體驗，使用的優點<xref:System.Windows.MessageBox>是，視窗會顯示由部分信任安全性沙箱中執行的應用程式的唯一類型 (請參閱[安全性](../../../../docs/framework/wpf/security-wpf.md))，例如[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]。  
  
 大多數對話方塊所顯示及收集的資料會比訊息方塊的結果更複雜，包括文字、選取範圍 (核取方塊)、互斥選取範圍 (選項按鈕)，以及清單選取範圍 (清單方塊、下拉式方塊、下拉式清單方塊)。 對於這些 Windows Presentation Foundation (WPF) 提供數個通用對話方塊，並可讓您建立您自己的對話方塊中，雖然任一個的使用受到以完全信任執行的應用程式。  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>通用對話方塊  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 實作所有應用程式通用之各種可重複使用的對話方塊，包括用於開啟檔案、儲存檔案和列印的對話方塊。 由於這些對話方塊是由作業系統實作，因此可在作業系統上執行的所有應用程式之間共用，以協助確保使用者體驗的一致性；當使用者在一個應用程式中熟悉如何使用某個作業系統提供的對話方塊時，就不需要了解如何在其他應用程式中使用該對話方塊。 因為這些對話方塊的所有應用程式可以使用，因為它們可以協助提供一致的使用者體驗，其稱為*通用對話方塊*。  
  
 Windows Presentation Foundation (WPF) 封裝開啟檔案、 儲存檔案，並列印通用對話方塊和其公開為 managed 的類別，供您使用獨立應用程式中。 本主題提供每個對話方塊的簡短概觀。  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>開啟檔案對話方塊  
 如下圖所示，檔案開啟功能使用 [開啟檔案] 對話方塊，來擷取要開啟之檔案的名稱。  
  
 ![開啟對話方塊](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure2.png "DialogBoxesOverviewFigure2")  
  
 常見的開啟檔案對話方塊會實作為<xref:Microsoft.Win32.OpenFileDialog>類別，且其位於<xref:Microsoft.Win32>命名空間。 下列程式碼示範如何建立、設定及顯示一個對話方塊，以及如何處理結果。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 如需 [開啟檔案] 對話方塊的詳細資訊，請參閱<xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>。  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog> 可以用來安全地擷取檔案名稱，以部分信任執行的應用程式 (請參閱[安全性](../../../../docs/framework/wpf/security-wpf.md))。  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>儲存檔案對話方塊  
 如下圖所示，檔案儲存功能使用 [儲存檔案] 對話方塊，來擷取要儲存之檔案的名稱。  
  
 ![另存新檔對話方塊](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure3.png "DialogBoxesOverviewFigure3")  
  
 儲存檔案 對話方塊的一般會實作為<xref:Microsoft.Win32.SaveFileDialog>類別，且其位於<xref:Microsoft.Win32>命名空間。 下列程式碼示範如何建立、設定及顯示一個對話方塊，以及如何處理結果。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 如需詳細資訊，在儲存檔案 對話方塊，請參閱<xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>。  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>列印對話方塊  
 如下圖所示，列印功能使用 [列印] 對話方塊，來選擇及設定使用者想要列印資料的目標印表機。  
  
 ![列印對話方塊](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure4.png "DialogBoxesOverviewFigure4")  
  
 通用列印對話方塊會實作為<xref:System.Windows.Controls.PrintDialog>類別，且其位於<xref:System.Windows.Controls>命名空間。 下列程式碼示範如何建立、設定及顯示一個對話方塊。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 如需有關 [列印] 對話方塊的詳細資訊，請參閱<xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>。 如列印中詳細討論[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，請參閱[列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)。  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>自訂對話方塊  
 雖然通用對話方塊很有用，而且應該盡可能使用，但這類對話方塊並不支援定義域專屬對話方塊的需求。 在此情況下，您必須建立自己的對話方塊。 如稍後所示，對話方塊是具有特殊行為的視窗。 <xref:System.Windows.Window> 實作這些行為，因此，您使用<xref:System.Windows.Window>建立自訂強制回應和非強制回應對話方塊。  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>建立自訂強制回應對話方塊  
 本主題示範如何使用<xref:System.Windows.Window>建立一般的強制回應對話方塊方塊實作中，使用`Margins`對話方塊中，做為範例 (請參閱[對話方塊範例](http://go.microsoft.com/fwlink/?LinkID=159984))。 `Margins`對話方塊會顯示在下圖中。  
  
 ![邊界對話方塊](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure5.png "DialogBoxesOverviewFigure5")  
  
#### <a name="configuring-a-modal-dialog-box"></a>設定強制回應對話方塊  
 一般對話方塊的使用者介面包括：  
  
-   收集想要的資料所需的各種控制項。  
  
-   顯示**確定**按鈕，使用者按一下以關閉對話方塊，返回函式，並繼續處理。  
  
-   顯示**取消**按鈕讓使用者按一下以關閉對話方塊，並停止進一步處理的函式。  
  
-   顯示**關閉**標題列中的按鈕。  
  
-   顯示圖示。  
  
-   顯示**最小化**，**最大化**，和**還原**按鈕。  
  
-   顯示**系統**功能表來最小化、 最大化、 還原及關閉對話方塊。  
  
-   在開啟對話方塊的視窗上方和中央開啟。  
  
-   對話方塊的大小應該盡可能可供調整，以防止對話方塊過小，並提供使用者實用的預設大小，您必須分別設定預設大小和大小下限。  
  
-   按 ESC 鍵應該設定為鍵盤快速鍵，讓**取消**按的按鈕。 這藉由設定<xref:System.Windows.Controls.Button.IsCancel%2A>屬性**取消**按鈕`true`。  
  
-   按下 ENTER （或傳回） 的索引鍵應設定為鍵盤快速鍵，讓**確定**按的按鈕。 這藉由設定<xref:System.Windows.Controls.Button.IsDefault%2A>屬性**確定**按鈕`true`。  
  
 下列程式碼示範這項設定。  
  
 [!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup2)]  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind2)]  
  
 對話方塊的使用者體驗也會延伸至開啟對話方塊之視窗的功能表列。 當功能表項目所執行的函式需要透過對話方塊進行使用者互動才能繼續時，該函式的功能表項目會在其標頭中顯示省略符號，如下所示。  
  
 [!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup1)]  
[!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup2)]  
  
 當功能表項目所執行的函式顯示不需要使用者互動的對話方塊時 (例如 [關於] 對話方塊)，則不需要省略符號。  
  
#### <a name="opening-a-modal-dialog-box"></a>開啟強制回應對話方塊  
 對話方塊通常是使用者選取功能表項目以執行定義域專屬函式所顯示的結果，例如在文書處理器中設定文件的邊界。 將視窗顯示為對話方塊類似於顯示標準視窗，不過需要進行額外的對話方塊專屬設定。 具現化、設定及開啟對話方塊的整個過程如下列程式碼所示。  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind4)]  
  
 這裡的程式碼會將預設資訊 (目前邊界) 傳遞給對話方塊。 它也會設定<xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType>屬性會顯示對話方塊視窗的參考。 一般情況下，您應該一律設定對話方塊的擁有者，以提供視窗與狀態相關行為通用於所有對話方塊 (請參閱[WPF Windows 概觀](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)如需詳細資訊)。  
  
> [!NOTE]
>  您必須提供擁有者，以支援[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]自動化對話方塊 (請參閱[UI 自動化概觀](../../../../docs/framework/ui-automation/ui-automation-overview.md))。  
  
 對話方塊中設定之後，它會顯示為強制回應藉由呼叫<xref:System.Windows.Window.ShowDialog%2A>方法。  
  
#### <a name="validating-user-provided-data"></a>驗證使用者提供的資料  
 在開啟對話方塊且使用者提供所需資料之後，對話方塊會基於下列原因負責確保提供的資料有效：  
  
-   從安全性的觀點來看，應該驗證所有輸入。  
  
-   從定義域專屬的觀點來看，資料驗證可以防止程式碼處理錯誤的資料，這可能會擲回例外狀況。  
  
-   從使用者體驗的觀點來看，對話方塊可藉由對使用者顯示哪些輸入的資料無效來協助使用者。  
  
-   從效能的觀點來看，多層式應用程式中的資料驗證可以減少用戶層與應用程式層之間的來回行程次數，特別是當應用程式是由 Web 服務或伺服器架構資料庫組成時。  
  
 若要驗證繫結的控制項中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，您需要定義驗證規則並將它與繫結產生關聯。 驗證規則是自訂的類別衍生自<xref:System.Windows.Controls.ValidationRule>。 下列範例示範驗證規則， `MarginValidationRule`，繫結的值是用來檢查<xref:System.Double>，並且在指定範圍內。  
  
 [!code-csharp[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs#marginvalidationrulecode)]
 [!code-vb[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb#marginvalidationrulecode)]  
  
 在這段程式碼，驗證規則的驗證邏輯會實作覆寫<xref:System.Windows.Controls.ValidationRule.Validate%2A>方法，它會驗證資料，並傳回適當<xref:System.Windows.Controls.ValidationResult>。  
  
 若要建立驗證規則與繫結控制項的關聯，您可以使用下列標記。  
  
 [!code-xaml[DialogBoxSample#MarginsValidationMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup2)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup3)]  
  
 一旦驗證規則產生關聯之後,[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]將時會自動套用其繫結控制項中輸入的資料。 當控制項包含無效的資料，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]如下圖所示，將會顯示無效的控制，紅色框線。  
  
 ![無效的左邊界](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure7.png "DialogBoxesOverviewFigure7")  
  
 在使用者輸入有效的資料之前，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 不會將使用者侷限在無效的控制項。 這是很好的對話方塊行為；使用者應該能夠自由地巡覽對話方塊中的控制項，而不論資料是否有效。 不過，這表示使用者可以輸入無效的資料，然後按**確定** 按鈕。 基於這個理由，您的程式碼也需要驗證 對話方塊中的所有控制項方塊時**確定**處理按下按鍵時<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind3)]  
  
 這段程式碼會列舉在視窗上的所有相依性物件和任何無效時 (傳回<xref:System.Windows.Controls.Validation.GetHasError%2A>，無效的控制項取得焦點，`IsValid`方法會傳回`false`，和視窗會被視為無效。  
  
 一旦對話方塊有效，就可以安全地將它關閉並傳回。 在傳回過程中，必須將結果傳回呼叫函式。  
  
#### <a name="setting-the-modal-dialog-result"></a>設定強制回應對話方塊結果  
 開啟對話方塊方塊中，使用<xref:System.Windows.Window.ShowDialog%2A>基本上就像是呼叫的方法： 對話方塊方塊使用開啟的程式碼<xref:System.Windows.Window.ShowDialog%2A>等待，直到<xref:System.Windows.Window.ShowDialog%2A>傳回。 當<xref:System.Windows.Window.ShowDialog%2A>傳回、 程式碼需要呼叫它來決定是否要繼續處理還是停止處理，根據使用者按下**確定**按鈕或**取消** 按鈕。 若要簡化這項決策，對話方塊需要傳回使用者的選擇為<xref:System.Boolean>從傳回的值<xref:System.Windows.Window.ShowDialog%2A>方法。  
  
 當**確定**按一下按鈕時，<xref:System.Windows.Window.ShowDialog%2A>應該傳回`true`。 這藉由設定<xref:System.Windows.Window.DialogResult%2A>屬性對話方塊的方塊時**確定**按鈕。  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind3)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind4)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind4)]  
  
 請注意，<xref:System.Windows.Window.DialogResult%2A>屬性也會使視窗關閉自動，這可免除需要明確地呼叫<xref:System.Windows.Window.Close%2A>。  
  
 當**取消**按一下按鈕時，<xref:System.Windows.Window.ShowDialog%2A>應該傳回`false`，如此也必須設定<xref:System.Windows.Window.DialogResult%2A>屬性。  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind3)]  
  
 當按鈕的<xref:System.Windows.Controls.Button.IsCancel%2A>屬性設定為`true`且使用者按下 **取消**按鈕或 ESC 鍵<xref:System.Windows.Window.DialogResult%2A>會自動設為`false`。 下列標記具有相同的效果上述程式碼，而不需要處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
 [!code-xaml[DialogBoxSample#MarginsDialogDefaultCancelMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogdefaultcancelmarkup)]  
  
 對話方塊會自動傳回`false`當使用者按下**關閉**按鈕標題列中，或選擇**關閉**功能表項目從**系統**功能表。  
  
#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>處理從強制回應對話方塊傳回的資料  
 當<xref:System.Windows.Window.DialogResult%2A>設定的對話方塊中，開啟它的函式可以藉由檢查取得對話方塊結果<xref:System.Windows.Window.DialogResult%2A>屬性時<xref:System.Windows.Window.ShowDialog%2A>傳回。  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind4)]  
  
 如果對話方塊結果`true`，函式使用該值做為提示來擷取及處理使用者所提供的資料。  
  
> [!NOTE]
>  之後<xref:System.Windows.Window.ShowDialog%2A>已傳回，無法重新開啟對話方塊。 您必須改為建立新的執行個體。  
  
 如果對話方塊結果`false`，函式應該適當地結束處理。  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>建立自訂非強制回應對話方塊  
 非強制回應對話方塊 (例如下圖所示的 [尋找] 對話方塊) 與強制回應對話方塊具有相同的基本外觀。  
  
 ![尋找對話方塊](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure6.PNG "DialogBoxesOverviewFigure6")  
  
 不過，其行為稍有不同，如下列各節中所述。  
  
#### <a name="opening-a-modeless-dialog-box"></a>開啟非強制回應對話方塊  
 非強制回應對話方塊開啟藉由呼叫<xref:System.Windows.Window.Show%2A>方法。  
  
 [!code-xaml[DialogBoxSample#OpenFindDialogMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#openfinddialogmarkup1)]  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind3)]  
  
 不同於<xref:System.Windows.Window.ShowDialog%2A>，<xref:System.Windows.Window.Show%2A>會立即傳回。 因此，呼叫視窗無法得知非強制回應對話方塊何時關閉，因此不會知道何時要檢查對話方塊結果，或從對話方塊取得資料以進一步處理。 相反地，對話方塊必須建立其他方式，以將資料傳回呼叫視窗進行處理。  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>處理從非強制回應對話方塊傳回的資料  
 在此範例中，`FindDialogBox`可能會傳回一或多個尋找結果到主視窗中，根據不含任何特定的頻率所搜尋的文字。 如同強制回應對話方塊，非強制回應對話方塊可以透過屬性傳回結果。 不過，主控對話方塊的視窗必須知道何時要查看這些屬性。 其中一個做法是，讓對話方塊實作每次找到文字時所引發的事件。 `FindDialogBox` 實作`TextFoundEvent`基於此目的，會先需要委派。  
  
 [!code-csharp[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs#textfoundeventhandlercode)]
 [!code-vb[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb#textfoundeventhandlercode)]  
  
 使用`TextFoundEventHandler`委派，`FindDialogBox`實作`TextFoundEvent`。  
  
 [!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind2)]  
  
 因此，`Find`可以引發事件時找到搜尋結果。  
  
 [!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind2)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind3)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind3)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind4)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind4)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind5)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind5)]  
  
 主控視窗接著需要註冊及處理此事件。  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind2)]  
  
#### <a name="closing-a-modeless-dialog-box"></a>關閉非強制回應對話方塊  
 因為<xref:System.Windows.Window.DialogResult%2A>不需要設定，可以關閉非強制回應對話方塊，使用系統提供的機制，包括下列：  
  
-   按一下**關閉**標題列中的按鈕。  
  
-   按下 ALT+F4。  
  
-   選擇**關閉**從**系統**功能表。  
  
 或者，您的程式碼可以呼叫<xref:System.Windows.Window.Close%2A>時**關閉**按鈕。  
  
 [!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind1)]
 [!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind1)]  
[!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind2)]
[!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind2)]  
  
## <a name="see-also"></a>另請參閱  
 [快顯功能表概觀](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [對話方塊範例](http://go.microsoft.com/fwlink/?LinkID=159984)  
 [ColorPicker Custom Control Sample](http://go.microsoft.com/fwlink/?LinkID=159977) (ColorPicker 自訂控制項範例)
