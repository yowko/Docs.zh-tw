---
title: "對話方塊概觀 | Microsoft Docs"
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
  - "非強制回應對話方塊"
  - "對話方塊"
  - "訊息方塊"
  - "強制回應對話方塊"
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# 對話方塊概觀
獨立應用程式通常具有主視窗，同時會顯示哪些應用程式運作且公開的功能來處理該資料的主要資料[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]機制喜歡功能表列、 工具列和狀態列。 重要的應用程式可能也會顯示其他視窗執行下列操作︰  
  
-   對使用者顯示的特定資訊。  
  
-   從使用者收集資訊。  
  
-   顯示並收集資訊。  
  
 這些類型的 windows 稱為*對話方塊*，而且有兩種類型︰ 強制回應和非強制回應。  
  
 A*強制回應*函式需要使用者繼續從其他資料時，對話方塊隨即顯示函式。 函式取決於強制回應對話方塊來收集資料，因為強制回應對話方塊也可避免使用者啟動應用程式中的其他視窗，雖然它保持開啟。 在大部分情況下，強制回應對話方塊，讓使用者能夠藉由按下 [已完成的強制回應對話方塊時，發出訊號**確定**或**取消**] 按鈕。 按下**確定**按鈕表示使用者已輸入的資料，而且想要繼續處理該資料的函式。 按下**取消**按鈕表示使用者想要停止執行的函式。 開啟、 儲存和列印資料顯示強制回應對話方塊的最常見的範例。  
  
 A*非強制回應*對話方塊中，相反地，不會防止使用者啟動其他視窗開啟時。 比方說，如果使用者想要在文件中尋找特定字的出現次數，主視窗通常會開啟對話方塊，詢問使用者哪些他們要尋找的單字。 因為尋找文字並不會防止使用者編輯文件，不過，對話方塊中不需要是強制回應。 非強制回應對話方塊至少提供**關閉** 按鈕以關閉對話方塊，並可能會提供其他按鈕來執行特定函式，例如**尋找下一個**按鈕來尋找下一個符合之搜尋準則的文字搜尋的文字。  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]可讓您建立數種類型的對話方塊，包括訊息方塊、 通用對話方塊，以及自訂對話方塊。 本主題將討論每個，而[對話方塊範例](http://go.microsoft.com/fwlink/?LinkID=159984)提供相符的範例。  
  
   
  
<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>訊息方塊  
 A*訊息方塊*是可用來顯示文字資訊，並允許使用者使用按鈕進行決策的對話方塊。 下圖顯示的文字資訊、 提出問題，並提供使用者回答這個問題的三個按鈕的訊息方塊。  
  
 ![文書處理器對話方塊](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure1.png "DialogBoxesOverviewFigure1")  
  
 若要建立訊息方塊，您使用<xref:System.Windows.MessageBox>類別。                  <xref:System.Windows.MessageBox>可讓您設定訊息方塊文字、 標題、 圖示和按鈕，使用程式碼如下所示。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 若要顯示的訊息方塊，請呼叫`static`<xref:System.Windows.MessageBox.Show%2A>方法，如下列程式碼所示。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 時顯示訊息方塊的程式碼必須偵測及處理使用者的決策 （哪一個按鈕已按下），程式碼可以檢查訊息方塊的結果，如下列程式碼所示。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 如需有關如何使用訊息方塊的詳細資訊，請參閱<xref:System.Windows.MessageBox>， [MessageBox 範例](http://go.microsoft.com/fwlink/?LinkID=160023)，和[對話方塊範例](http://go.microsoft.com/fwlink/?LinkID=159984)。  
  
 雖然<xref:System.Windows.MessageBox>可能會提供簡單的對話方塊方塊的使用者經驗，使用的優點<xref:System.Windows.MessageBox> ，是可以在部分信任安全性沙箱中執行的應用程式所顯示的視窗的唯一類型 (請參閱[安全性](../../../../docs/framework/wpf/security-wpf.md))，例如[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]。  
  
 大部份的對話方塊會顯示和收集更複雜的資料，比結果的訊息方塊中，包括文字選取範圍 （核取方塊） 互斥的選項 （選項按鈕），並列出選取範圍 （清單方塊、 下拉式方塊、 下拉式清單方塊）。 對於這些[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]提供數個通用對話方塊，並可讓您建立您自己的對話方塊中，雖然上述任一種使用僅限於以完全信任執行的應用程式。  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>通用對話方塊  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]實作各種不同的可重複使用的對話方塊通用於所有應用程式，包括開啟檔案、 儲存檔案及列印的對話方塊。 這些對話方塊由作業系統實作的因為它們可以共用所有的作業系統，可協助使用者經驗的一致性; 執行的應用程式使用者熟悉的作業系統提供的對話方塊在應用程式中使用時，它們不需要了解如何使用其他應用程式在該對話方塊。 因為這些對話方塊分別是所有應用程式可用，因為它們可以協助提供一致的使用者經驗，這些運算式稱為*通用對話方塊*。  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]封裝開啟檔案，儲存檔案和列印的通用對話方塊，並為受管理的類別，供您使用獨立應用程式中將它們公開。 本主題提供的每個的簡要概觀。  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>開啟檔案 對話方塊  
 開啟檔案對話方塊中，顯示在下圖中，可供檔案開啟功能來擷取要開啟的檔案名稱。  
  
 ![開啟的對話方塊中](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure2.png "DialogBoxesOverviewFigure2")  
  
 常見的開啟檔案對話方塊會實作為<xref:Microsoft.Win32.OpenFileDialog>類別，而位於<xref:Microsoft.Win32>命名空間。 下列程式碼示範如何建立、 設定及顯示一個對話方塊，以及如何處理結果。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 如需有關開啟檔案對話方塊的詳細資訊，請參閱<xref:Microsoft.Win32.OpenFileDialog?displayProperty=fullName>。  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog>可以用來安全地擷取檔案名稱，以部分信任執行的應用程式 (請參閱[安全性](../../../../docs/framework/wpf/security-wpf.md))。  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>儲存檔案 對話方塊  
 儲存檔案對話方塊中，顯示在下圖中，使用檔案儲存功能來擷取要儲存檔案的名稱。  
  
 ![另存新檔 對話方塊中](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure3.png "DialogBoxesOverviewFigure3")  
  
 儲存檔案 對話方塊的一般會實作為<xref:Microsoft.Win32.SaveFileDialog>類別，而位於<xref:Microsoft.Win32>命名空間。 下列程式碼示範如何建立、 設定及顯示一個對話方塊，以及如何處理結果。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 如需詳細資訊，在儲存檔案 對話方塊，請參閱<xref:Microsoft.Win32.SaveFileDialog?displayProperty=fullName>。  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>列印對話方塊  
 列印功能會使用 [列印] 對話方塊下, 圖所示，選擇及設定使用者想要的資料列印至印表機。  
  
 ![列印對話方塊](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure4.png "DialogBoxesOverviewFigure4")  
  
 通用列印對話方塊會實作為<xref:System.Windows.Controls.PrintDialog>類別，而位於<xref:System.Windows.Controls>命名空間。 下列程式碼示範如何建立、 設定及顯示一個。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 如需有關 [列印] 對話方塊的詳細資訊，請參閱<xref:System.Windows.Controls.PrintDialog?displayProperty=fullName>。 如在列印的詳細討論[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，請參閱[列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)。  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>自訂對話方塊  
 當通用對話方塊十分有用，而且應該盡可能使用時，它們不支援需求的網域特定的對話方塊。 在這些情況下，您需要建立自己的對話方塊。 如我們所見，對話方塊就會是具有特殊行為的視窗。                  <xref:System.Windows.Window>實作這些行為，因此，您使用<xref:System.Windows.Window>來建立自訂強制回應和非強制回應對話方塊。  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>建立自訂強制回應對話方塊  
 本主題說明如何使用<xref:System.Windows.Window>建立一般的強制回應對話方塊方塊實作中，使用`Margins` 對話方塊中，做為範例 (請參閱[對話方塊範例](http://go.microsoft.com/fwlink/?LinkID=159984))。 `Margins`對話方塊會顯示如下圖所示。  
  
 ![邊界對話方塊](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure5.png "DialogBoxesOverviewFigure5")  
  
#### <a name="configuring-a-modal-dialog-box"></a>設定強制回應對話方塊  
 一般對話方塊的使用者介面包含下列內容︰  
  
-   收集所需的資料所需的各種控制項。  
  
-   顯示**確定**使用者按一下以關閉對話方塊，返回函式，並繼續處理 按鈕。  
  
-   顯示**取消**按鈕讓使用者按一下以關閉對話方塊，並停止進一步處理的函式。  
  
-   顯示**關閉**標題列中的按鈕。  
  
-   顯示圖示。  
  
-   Showing                                          **Minimize**,                                          **Maximize**, and                                          **Restore** buttons.  
  
-   顯示**系統**功能表來最小化、 最大化、 還原及關閉對話方塊。  
  
-   開啟的上面和中央的 [開啟] 對話方塊中的視窗。  
  
-   對話方塊應該分別是有可能，因此若要防止對話方塊太小，並提供使用者最有用的預設大小，您必須設定預設值和最小值，可調整大小的維度。  
  
-   按 ESC 鍵應設定為鍵盤快速鍵使**取消**按鈕被按下。 這藉由設定<xref:System.Windows.Controls.Button.IsCancel%2A>屬性**取消**按鈕`true`。  
  
-   按下 ENTER （或傳回） 的索引鍵應設定為鍵盤快速鍵使**確定**按鈕被按下。 這藉由設定<xref:System.Windows.Controls.Button.IsDefault%2A>屬性**確定**按鈕`true`。  
  
 下列程式碼示範這項設定。  
  
 [!code-xml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup1)]  
[!code-xml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup2)]  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind2)]  
  
 對話方塊中的使用者經驗也會延伸至功能表列的 [開啟] 對話方塊中的視窗。 功能表項目執行時需要使用者互動，透過 對話方塊中，才能繼續執行函式的函式，函式的功能表項目都會在省略符號標頭，如下所示。  
  
 [!code-xml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup1)]  
[!code-xml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup2)]  
  
 如果功能表項目執行函式，以顯示對話方塊，不需要使用者互動，例如 [關於] 對話方塊中，則不需要省略符號。  
  
#### <a name="opening-a-modal-dialog-box"></a>開啟強制回應對話方塊  
 對話方塊通常顯示的結果，使用者選取功能表項目執行定義域專屬的功能，例如設定文書處理器中的文件的邊界。 顯示為對話方塊視窗如下顯示標準的視窗中，雖然它所需的其他對話方塊 方塊中特定的組態。 具現化的整個程序，設定與開啟的對話方塊會顯示下列程式碼中。  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind4)]  
  
 在這裡，程式碼會傳遞至對話方塊的預設資訊 （目前邊界）。 它也會設定<xref:System.Windows.Window.Owner%2A?displayProperty=fullName>屬性會顯示對話方塊視窗的參考。 一般情況下，您必須一律設定對話方塊的擁有者提供的視窗狀態相關行為通用於所有的對話方塊 (請參閱[WPF 視窗概觀](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)如需詳細資訊)。  
  
> [!NOTE]
>  您必須提供擁有者，以支援[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]自動化對話方塊 (請參閱[UI 自動化概觀](../../../../docs/framework/ui-automation/ui-automation-overview.md))。  
  
 對話方塊中設定之後，它會顯示強制回應藉由呼叫<xref:System.Windows.Window.ShowDialog%2A>方法。  
  
#### <a name="validating-user-provided-data"></a>驗證使用者所提供的資料  
 當對話方塊開啟時，使用者會提供所需的資料 對話方塊中負責提供的資料無效，原因如下︰  
  
-   從安全性角度來看，您應該驗證所有輸入。  
  
-   定義域專屬的觀點而言，資料驗證可防止錯誤的資料處理的程式碼，可能會擲回例外狀況。  
  
-   使用者經驗的觀點而言，對話方塊可以協助使用者以顯示使用者輸入的資料無效。  
  
-   從效能觀點來看，特別是當應用程式由 Web 服務或伺服器端資料庫構成多層式應用程式中的資料驗證時，可以減少用戶端與應用程式各層之間的往返次數。  
  
 若要驗證繫結的控制項中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，您需要定義驗證規則，並將它與繫結產生關聯。 驗證規則是自訂的類別衍生自<xref:System.Windows.Controls.ValidationRule>。 下列範例示範的驗證規則， `MarginValidationRule`，繫結的值是用來檢查<xref:System.Double>和指定的範圍內。  
  
 [!code-csharp[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs#marginvalidationrulecode)]
 [!code-vb[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb#marginvalidationrulecode)]  
  
 在這段程式碼，驗證規則的驗證邏輯實作的覆寫<xref:System.Windows.Controls.ValidationRule.Validate%2A>方法，它會驗證資料並傳回適當<xref:System.Windows.Controls.ValidationResult>。  
  
 若要將驗證規則與繫結的控制項產生關聯，您可以使用下列標記。  
  
 [!code-xml[DialogBoxSample#MarginsValidationMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup1)]  
[!code-xml[DialogBoxSample#MarginsValidationMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup2)]  
[!code-xml[DialogBoxSample#MarginsValidationMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup3)]  
  
 當驗證規則建立關聯之後,[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]會自動將它套用時輸入的資料繫結的控制項。 當控制項包含無效的資料，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]會顯示紅色無效的控制項框線，如下圖所示。  
  
 ![無效的左邊的界](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure7.png "DialogBoxesOverviewFigure7")  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]不會限制使用者無效的控制項，直到使用者輸入有效的資料。 這是恰當的對話方塊。使用者應該能夠自由地瀏覽 對話方塊中的控制項，不論資料有效。 不過，這表示使用者可以輸入無效的資料，然後按**確定** 按鈕。 基於這個理由，您的程式碼也需要驗證 對話方塊中的所有控制項方塊時**確定**處理按下按鈕時<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind3)]  
  
 此程式碼會列舉在視窗上的所有相依性物件和任何無效時 (所傳回的<xref:System.Windows.Controls.Validation.GetHasError%2A>，無效的控制項取得焦點，`IsValid`方法會傳回`false`，和視窗會被視為無效。  
  
 一旦對話方塊是有效的它就可以安全地關閉，並傳回。 傳回的程序的一部分，它必須將結果傳回給呼叫的函式。  
  
#### <a name="setting-the-modal-dialog-result"></a>設定強制回應對話方塊結果  
 開啟 [對話方塊] 方塊中，使用<xref:System.Windows.Window.ShowDialog%2A>基本上就像是呼叫的方法︰ 開啟對話方塊方塊使用的程式碼<xref:System.Windows.Window.ShowDialog%2A>等待，直到<xref:System.Windows.Window.ShowDialog%2A>傳回。 當<xref:System.Windows.Window.ShowDialog%2A>傳回，程式碼需要呼叫它來決定是否要繼續處理，或停止處理，根據使用者按下**確定**按鈕或**取消** 按鈕。 若要簡化這項決策，對話方塊需要傳回做為使用者的選擇<xref:System.Boolean>所傳回的值<xref:System.Windows.Window.ShowDialog%2A>方法。  
  
 當**確定**按一下按鈕時， <xref:System.Windows.Window.ShowDialog%2A>應該會傳回`true`。 這藉由設定<xref:System.Windows.Window.DialogResult%2A>屬性 對話方塊的方塊時**確定**按鈕時。  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind3)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind4)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind4)]  
  
 請注意， <xref:System.Windows.Window.DialogResult%2A>屬性也會使視窗關閉自動，這可免除需要明確地呼叫<xref:System.Windows.Window.Close%2A>。  
  
 當**取消**按一下按鈕時， <xref:System.Windows.Window.ShowDialog%2A>應該會傳回`false`，這也需要設定<xref:System.Windows.Window.DialogResult%2A>屬性。  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind3)]  
  
 當按鈕<xref:System.Windows.Controls.Button.IsCancel%2A>屬性設定為`true`且使用者按下 **取消**按鈕或 ESC 鍵<xref:System.Windows.Window.DialogResult%2A>會自動設為`false`。 下列標記有上述的程式碼，而不需要處理相同的效果<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
 [!code-xml[DialogBoxSample#MarginsDialogDefaultCancelMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogdefaultcancelmarkup)]  
  
 對話方塊會自動傳回`false`當使用者按下**關閉**標題列中按鈕或選擇**關閉**功能表項目從**系統**功能表。  
  
#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>處理從強制回應對話方塊傳回的資料  
 當<xref:System.Windows.Window.DialogResult%2A>設定對話方塊中，開啟它的函式可以藉由檢查取得對話方塊結果<xref:System.Windows.Window.DialogResult%2A>屬性時<xref:System.Windows.Window.ShowDialog%2A>傳回。  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind4)]  
  
 如果對話方塊結果是`true`，函式使用該值做為提示來擷取及處理使用者所提供的資料。  
  
> [!NOTE]
>  之後<xref:System.Windows.Window.ShowDialog%2A>已傳回，無法重新開啟對話方塊。 相反地，您需要建立新的執行個體。  
  
 如果對話方塊結果是`false`，函式應該適當地結束處理。  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>建立自訂非強制回應對話方塊  
 非強制回應對話方塊，例如 [尋找] 對話方塊顯示在下圖中，有基本的外觀相同為強制回應對話方塊。  
  
 ![尋找對話方塊](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure6.PNG "DialogBoxesOverviewFigure6")  
  
 不過，行為都稍有不同，如下列各節中所述。  
  
#### <a name="opening-a-modeless-dialog-box"></a>開啟非強制回應對話方塊  
 非強制回應對話方塊開啟藉由呼叫<xref:System.Windows.Window.Show%2A>方法。  
  
 [!code-xml[DialogBoxSample#OpenFindDialogMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#openfinddialogmarkup1)]  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind3)]  
  
 不同於<xref:System.Windows.Window.ShowDialog%2A>，<xref:System.Windows.Window.Show%2A>會立即傳回。 因此，呼叫視窗不知道當非強制回應對話方塊已關閉，因此，不知道何時要檢查的對話方塊結果，或從對話方塊中取得資料，供進一步處理。 相反地，對話方塊需要建立將資料傳回給呼叫視窗以進行處理的替代方式。  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>處理從非強制回應對話方塊傳回的資料  
 在此範例中，`FindDialogBox`可能會傳回一或多個尋找主視窗中，根據文字而不需要任何特定的頻率要搜尋的結果。 如同非強制回應對話方塊，非強制回應對話方塊可能會傳回使用屬性的結果。 不過，擁有對話方塊的視窗必須知道何時要檢查這些屬性。 若要啟用此功能的方法之一是實作每當找到文字就會引發事件之對話方塊。                                  `FindDialogBox`實作`TextFoundEvent`基於此目的，會先需要委派。  
  
 [!code-csharp[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs#textfoundeventhandlercode)]
 [!code-vb[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb#textfoundeventhandlercode)]  
  
 Using the                                  `TextFoundEventHandler` delegate,                                  `FindDialogBox` implements the                                  `TextFoundEvent`.  
  
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
  
 主控視窗則需要註冊，並處理這個事件。  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind2)]  
  
#### <a name="closing-a-modeless-dialog-box"></a>關閉非強制回應對話方塊  
 因為<xref:System.Windows.Window.DialogResult%2A>不需要設定，可關閉非強制回應對話方塊，使用系統提供的機制，包括下列︰  
  
-   按一下**關閉**標題列中的按鈕。  
  
-   按 ALT + F4。  
  
-   Choosing                                          **Close** from the                                          **System** menu.  
  
 或者，您的程式碼可以呼叫<xref:System.Windows.Window.Close%2A>時**關閉**按鈕時。  
  
 [!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind1)]
 [!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind1)]  
[!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind2)]
[!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind2)]  
  
## <a name="see-also"></a>另請參閱  
 [快顯功能表概觀](../../../../docs/framework/wpf/controls/popup-overview.md)   
 [對話方塊範例](http://go.microsoft.com/fwlink/?LinkID=159984)   
 [ColorPicker 自訂控制項範例](http://go.microsoft.com/fwlink/?LinkID=159977)