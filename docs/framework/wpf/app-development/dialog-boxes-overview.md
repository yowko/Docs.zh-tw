---
title: 對話方塊概觀
description: 瞭解您可以用來收集和顯示資訊的 Windows Foundation 簡報（WPF）中各種對話方塊。
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
ms.openlocfilehash: 822604dd694f2f6260496872fd7a1a8440a62535
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618138"
---
# <a name="dialog-boxes-overview"></a><span data-ttu-id="0082d-103">對話方塊總覽</span><span class="sxs-lookup"><span data-stu-id="0082d-103">Dialog boxes overview</span></span>
<span data-ttu-id="0082d-104">獨立應用程式通常會有一個主視窗，它會顯示應用程式運作的主要資料，並透過 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 功能表列、工具列和狀態列等機制來公開處理該資料的功能。</span><span class="sxs-lookup"><span data-stu-id="0082d-104">Standalone applications typically have a main window that both displays the main data over which the application operates and exposes the functionality to process that data through [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mechanisms like menu bars, tool bars, and status bars.</span></span> <span data-ttu-id="0082d-105">重要的應用程式還可能顯示其他視窗來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0082d-105">A non-trivial application may also display additional windows to do the following:</span></span>  
  
- <span data-ttu-id="0082d-106">對使用者顯示特定資訊。</span><span class="sxs-lookup"><span data-stu-id="0082d-106">Display specific information to users.</span></span>  
  
- <span data-ttu-id="0082d-107">向使用者收集資訊。</span><span class="sxs-lookup"><span data-stu-id="0082d-107">Gather information from users.</span></span>  
  
- <span data-ttu-id="0082d-108">顯示並收集資訊。</span><span class="sxs-lookup"><span data-stu-id="0082d-108">Both display and gather information.</span></span>  
  
 <span data-ttu-id="0082d-109">這些類型的視窗稱為*對話方塊*，而且有兩種類型：強制回應和非強制回應。</span><span class="sxs-lookup"><span data-stu-id="0082d-109">These types of windows are known as *dialog boxes*, and there are two types: modal and modeless.</span></span>  
  
 <span data-ttu-id="0082d-110">當函式需要使用者的其他資料才能繼續時，函數會顯示*模式*對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0082d-110">A *modal* dialog box is displayed by a function when the function needs additional data from a user to continue.</span></span> <span data-ttu-id="0082d-111">由於該函式需要透過強制回應對話方塊收集資料，因此當強制回應對話方塊保持開啟時，也可以防止使用者在應用程式中啟動其他視窗。</span><span class="sxs-lookup"><span data-stu-id="0082d-111">Because the function depends on the modal dialog box to gather data, the modal dialog box also prevents a user from activating other windows in the application while it remains open.</span></span> <span data-ttu-id="0082d-112">在大部分情況下，強制回應對話方塊可讓使用者在完成強制回應對話方塊時，按下 **[確定**] 或 [**取消**] 按鈕來發出信號。</span><span class="sxs-lookup"><span data-stu-id="0082d-112">In most cases, a modal dialog box allows a user to signal when they have finished with the modal dialog box by pressing either an **OK** or **Cancel** button.</span></span> <span data-ttu-id="0082d-113">按下 [**確定]** 按鈕，表示使用者已輸入資料，而且想要讓該函數繼續處理該資料。</span><span class="sxs-lookup"><span data-stu-id="0082d-113">Pressing the **OK** button indicates that a user has entered data and wants the function to continue processing with that data.</span></span> <span data-ttu-id="0082d-114">按下 [**取消**] 按鈕表示使用者想要完全停止執行函式。</span><span class="sxs-lookup"><span data-stu-id="0082d-114">Pressing the **Cancel** button indicates that a user wants to stop the function from executing altogether.</span></span> <span data-ttu-id="0082d-115">強制回應對話方塊的最常見範例為開啟、儲存及列印資料。</span><span class="sxs-lookup"><span data-stu-id="0082d-115">The most common examples of modal dialog boxes are shown to open, save, and print data.</span></span>  
  
 <span data-ttu-id="0082d-116">另一方面，非*模式*對話方塊則不會防止使用者在開啟其他視窗時加以啟用。</span><span class="sxs-lookup"><span data-stu-id="0082d-116">A *modeless* dialog box, on the other hand, does not prevent a user from activating other windows while it is open.</span></span> <span data-ttu-id="0082d-117">例如，如果使用者想要尋找出現在文件中的特定字組，主視窗通常會開啟對話方塊，詢問使用者要尋找哪個字組。</span><span class="sxs-lookup"><span data-stu-id="0082d-117">For example, if a user wants to find occurrences of a particular word in a document, a main window will often open a dialog box to ask a user what word they are looking for.</span></span> <span data-ttu-id="0082d-118">不過，由於尋找字組並不會防止使用者編輯文件，因此對話方塊不需要是強制回應。</span><span class="sxs-lookup"><span data-stu-id="0082d-118">Since finding a word doesn't prevent a user from editing the document, however, the dialog box doesn't need to be modal.</span></span> <span data-ttu-id="0082d-119">[非模式] 對話方塊至少會提供關閉對話方塊的 [**關閉**] 按鈕，而且可能會提供其他按鈕來執行特定函式，例如 **[尋找下一個]** 按鈕，以尋找符合文字搜尋搜尋準則的下一個單字。</span><span class="sxs-lookup"><span data-stu-id="0082d-119">A modeless dialog box at least provides a **Close** button to close the dialog box, and may provide additional buttons to execute specific functions, such as a **Find Next** button to find the next word that matches the find criteria of a word search.</span></span>  
  
 <span data-ttu-id="0082d-120">Windows Presentation Foundation （WPF）可讓您建立數種類型的對話方塊，包括訊息方塊、通用對話方塊和自訂對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0082d-120">Windows Presentation Foundation (WPF) allows you to create several types of dialog boxes, including message boxes, common dialog boxes, and custom dialog boxes.</span></span> <span data-ttu-id="0082d-121">本主題將討論每個，而[對話方塊範例](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)會提供相符的範例。</span><span class="sxs-lookup"><span data-stu-id="0082d-121">This topic discusses each, and the [Dialog Box Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox) provides matching examples.</span></span>  

<a name="Message_Boxes"></a>
## <a name="message-boxes"></a><span data-ttu-id="0082d-122">訊息方塊</span><span class="sxs-lookup"><span data-stu-id="0082d-122">Message boxes</span></span>  
 <span data-ttu-id="0082d-123">*訊息方塊*是可用來顯示文字資訊的對話方塊，可讓使用者使用按鈕進行決策。</span><span class="sxs-lookup"><span data-stu-id="0082d-123">A *message box* is a dialog box that can be used to display textual information and to allow users to make decisions with buttons.</span></span> <span data-ttu-id="0082d-124">下圖所示的訊息方塊顯示文字資訊、提出問題，並提供使用者三個按鈕來回答問題。</span><span class="sxs-lookup"><span data-stu-id="0082d-124">The following figure shows a message box that displays textual information, asks a question, and provides the user with three buttons to answer the question.</span></span>  
  
 ![[文字處理器] 對話方塊，詢問您是否要在應用程式關閉之前，先儲存檔的變更。](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 <span data-ttu-id="0082d-126">若要建立訊息方塊，請使用 <xref:System.Windows.MessageBox> 類別。</span><span class="sxs-lookup"><span data-stu-id="0082d-126">To create a message box, you use the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="0082d-127"><xref:System.Windows.MessageBox>可讓您使用如下所示的程式碼，設定訊息方塊文字、標題、圖示和按鈕。</span><span class="sxs-lookup"><span data-stu-id="0082d-127"><xref:System.Windows.MessageBox> lets you configure the message box text, title, icon, and buttons, using code like the following.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 <span data-ttu-id="0082d-128">若要顯示訊息方塊，您可以呼叫 `static` <xref:System.Windows.MessageBox.Show%2A> 方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="0082d-128">To show a message box, you call the `static`<xref:System.Windows.MessageBox.Show%2A> method, as demonstrated in the following code.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 <span data-ttu-id="0082d-129">當顯示訊息方塊的程式碼必須偵測及處理使用者的決定時 (按下哪個按鈕)，程式碼可以查看訊息方塊結果，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="0082d-129">When code that shows a message box needs to detect and process the user's decision (which button was pressed), the code can inspect the message box result, as shown in the following code.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 <span data-ttu-id="0082d-130">如需使用訊息方塊的詳細資訊，請參閱 <xref:System.Windows.MessageBox> 、 [MessageBox 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)和[對話方塊範例](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)。</span><span class="sxs-lookup"><span data-stu-id="0082d-130">For more information on using message boxes, see <xref:System.Windows.MessageBox>, [MessageBox Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox), and [Dialog Box Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox).</span></span>  
  
 <span data-ttu-id="0082d-131">雖然 <xref:System.Windows.MessageBox> 可能會提供簡單的對話方塊使用者體驗，但使用的優點 <xref:System.Windows.MessageBox> 是，在部分信任安全性沙箱（請參閱[安全性](../security-wpf.md)）中執行的應用程式（例如 XAML 瀏覽器應用程式（xbap））可以顯示唯一的視窗類型。</span><span class="sxs-lookup"><span data-stu-id="0082d-131">Although <xref:System.Windows.MessageBox> may offer a simple dialog box user experience, the advantage of using <xref:System.Windows.MessageBox> is that is the only type of window that can be shown by applications that run within a partial trust security sandbox (see [Security](../security-wpf.md)), such as XAML browser applications (XBAPs).</span></span>  
  
 <span data-ttu-id="0082d-132">大多數對話方塊所顯示及收集的資料會比訊息方塊的結果更複雜，包括文字、選取範圍 (核取方塊)、互斥選取範圍 (選項按鈕)，以及清單選取範圍 (清單方塊、下拉式方塊、下拉式清單方塊)。</span><span class="sxs-lookup"><span data-stu-id="0082d-132">Most dialog boxes display and gather more complex data than the result of a message box, including text, selection (check boxes), mutually exclusive selection (radio buttons), and list selection (list boxes, combo boxes, drop-down list boxes).</span></span> <span data-ttu-id="0082d-133">在這些情況下，Windows Presentation Foundation （WPF）提供數個常見的對話方塊，並可讓您建立自己的對話方塊，雖然僅限於以完全信任執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0082d-133">For these, Windows Presentation Foundation (WPF) provides several common dialog boxes and allows you to create your own dialog boxes, although the use of either is limited to applications running with full trust.</span></span>  
  
<a name="Common_Dialogs"></a>
## <a name="common-dialog-boxes"></a><span data-ttu-id="0082d-134">通用對話方塊</span><span class="sxs-lookup"><span data-stu-id="0082d-134">Common dialog boxes</span></span>  
 <span data-ttu-id="0082d-135">Windows 會執行各種可重複使用的對話方塊，通用於所有應用程式，包括用來開啟檔案、儲存檔案和列印的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0082d-135">Windows implements a variety of reusable dialog boxes that are common to all applications, including dialog boxes for opening files, saving files, and printing.</span></span> <span data-ttu-id="0082d-136">由於這些對話方塊是由作業系統實作，因此可在作業系統上執行的所有應用程式之間共用，以協助確保使用者體驗的一致性；當使用者在一個應用程式中熟悉如何使用某個作業系統提供的對話方塊時，就不需要了解如何在其他應用程式中使用該對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0082d-136">Since these dialog boxes are implemented by the operating system, they can be shared among all the applications that run on the operating system, which helps user experience consistency; when users are familiar with the use of an operating system-provided dialog box in one application, they don't need to learn how to use that dialog box in other applications.</span></span> <span data-ttu-id="0082d-137">因為這些對話方塊可供所有應用程式使用，而且因為它們有助於提供一致的使用者體驗，所以也稱為*通用對話方塊*。</span><span class="sxs-lookup"><span data-stu-id="0082d-137">Because these dialog boxes are available to all applications and because they help provide a consistent user experience, they are known as *common dialog boxes*.</span></span>  
  
 <span data-ttu-id="0082d-138">Windows Presentation Foundation （WPF）會封裝開啟的檔案、儲存檔案和列印通用對話方塊，並將它們公開為受控類別，供您在獨立應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="0082d-138">Windows Presentation Foundation (WPF) encapsulates the open file, save file, and print common dialog boxes and exposes them as managed classes for you to use in standalone applications.</span></span> <span data-ttu-id="0082d-139">本主題提供每個對話方塊的簡短概觀。</span><span class="sxs-lookup"><span data-stu-id="0082d-139">This topic provides a brief overview of each.</span></span>  
  
<a name="Open_File_Dialog"></a>
### <a name="open-file-dialog"></a><span data-ttu-id="0082d-140">開啟檔案對話方塊</span><span class="sxs-lookup"><span data-stu-id="0082d-140">Open File dialog</span></span>  
 <span data-ttu-id="0082d-141">如下圖所示，檔案開啟功能使用 [開啟檔案] 對話方塊，來擷取要開啟之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0082d-141">The open file dialog box, shown in the following figure, is used by file opening functionality to retrieve the name of a file to open.</span></span>  
  
 ![[開啟] 對話方塊，其中顯示要取出檔案的位置。](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 <span data-ttu-id="0082d-143">一般的 [開啟檔案] 對話方塊會實作為 <xref:Microsoft.Win32.OpenFileDialog> 類別，並位於 <xref:Microsoft.Win32> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="0082d-143">The common open file dialog box is implemented as the <xref:Microsoft.Win32.OpenFileDialog> class and is located in the <xref:Microsoft.Win32> namespace.</span></span> <span data-ttu-id="0082d-144">下列程式碼示範如何建立、設定及顯示一個對話方塊，以及如何處理結果。</span><span class="sxs-lookup"><span data-stu-id="0082d-144">The following code shows how to create, configure, and show one, and how to process the result.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 <span data-ttu-id="0082d-145">如需 [開啟檔案] 對話方塊的詳細資訊，請參閱 <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0082d-145">For more information on the open file dialog box, see <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0082d-146"><xref:Microsoft.Win32.OpenFileDialog>可以用來安全地透過以部分信任執行的應用程式來抓取檔案名（請參閱[安全性](../security-wpf.md)）。</span><span class="sxs-lookup"><span data-stu-id="0082d-146"><xref:Microsoft.Win32.OpenFileDialog> can be used to safely retrieve file names by applications running with partial trust (see [Security](../security-wpf.md)).</span></span>  
  
<a name="Save_File_Dialog"></a>
### <a name="save-file-dialog-box"></a><span data-ttu-id="0082d-147">儲存對話方塊</span><span class="sxs-lookup"><span data-stu-id="0082d-147">Save File dialog box</span></span>  
 <span data-ttu-id="0082d-148">如下圖所示，檔案儲存功能使用 [儲存檔案] 對話方塊，來擷取要儲存之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0082d-148">The save file dialog box, shown in the following figure, is used by file saving functionality to retrieve the name of a file to save.</span></span>  
  
 ![[另存新檔] 對話方塊，其中顯示儲存檔案的位置。](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 <span data-ttu-id="0082d-150">[一般儲存檔案] 對話方塊會實作為 <xref:Microsoft.Win32.SaveFileDialog> 類別，並位於 <xref:Microsoft.Win32> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="0082d-150">The common save file dialog box is implemented as the <xref:Microsoft.Win32.SaveFileDialog> class, and is located in the <xref:Microsoft.Win32> namespace.</span></span> <span data-ttu-id="0082d-151">下列程式碼示範如何建立、設定及顯示一個對話方塊，以及如何處理結果。</span><span class="sxs-lookup"><span data-stu-id="0082d-151">The following code shows how to create, configure, and show one, and how to process the result.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 <span data-ttu-id="0082d-152">如需 [儲存檔案] 對話方塊的詳細資訊，請參閱 <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0082d-152">For more information on the save file dialog box, see <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.</span></span>  
  
<a name="Print_Dialog"></a>
### <a name="print-dialog-box"></a><span data-ttu-id="0082d-153">列印對話方塊</span><span class="sxs-lookup"><span data-stu-id="0082d-153">Print dialog box</span></span>

<span data-ttu-id="0082d-154">如下圖所示，列印功能使用 [列印] 對話方塊，來選擇及設定使用者想要列印資料的目標印表機。</span><span class="sxs-lookup"><span data-stu-id="0082d-154">The print dialog box, shown in the following figure, is used by printing functionality to choose and configure the printer that a user would like to print data to.</span></span>  
  
![顯示 [列印] 對話方塊的螢幕擷取畫面。](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
<span data-ttu-id="0082d-156">一般 [列印] 對話方塊會實作為 <xref:System.Windows.Controls.PrintDialog> 類別，並位於 <xref:System.Windows.Controls> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="0082d-156">The common print dialog box is implemented as the <xref:System.Windows.Controls.PrintDialog> class, and is located in the <xref:System.Windows.Controls> namespace.</span></span> <span data-ttu-id="0082d-157">下列程式碼示範如何建立、設定及顯示一個對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0082d-157">The following code shows how to create, configure, and show one.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 <span data-ttu-id="0082d-158">如需 [列印] 對話方塊的詳細資訊，請參閱 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0082d-158">For more information on the print dialog box, see <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0082d-159">如需在 WPF 中列印的詳細討論，請參閱[列印總覽](../advanced/printing-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="0082d-159">For detailed discussion of printing in WPF, see [Printing Overview](../advanced/printing-overview.md).</span></span>  
  
<a name="Custom_Dialog_Boxes"></a>
## <a name="custom-dialog-boxes"></a><span data-ttu-id="0082d-160">自訂對話方塊</span><span class="sxs-lookup"><span data-stu-id="0082d-160">Custom dialog boxes</span></span>

<span data-ttu-id="0082d-161">雖然通用對話方塊很有用，而且應該盡可能使用，但這類對話方塊並不支援定義域專屬對話方塊的需求。</span><span class="sxs-lookup"><span data-stu-id="0082d-161">While common dialog boxes are useful, and should be used when possible, they do not support the requirements of domain-specific dialog boxes.</span></span> <span data-ttu-id="0082d-162">在此情況下，您必須建立自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0082d-162">In these cases, you need to create your own dialog boxes.</span></span> <span data-ttu-id="0082d-163">如稍後所示，對話方塊是具有特殊行為的視窗。</span><span class="sxs-lookup"><span data-stu-id="0082d-163">As we'll see, a dialog box is a window with special behaviors.</span></span> <span data-ttu-id="0082d-164"><xref:System.Windows.Window>會執行這些行為，因此，您可以使用 <xref:System.Windows.Window> 來建立自訂的強制回應和非強制回應對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0082d-164"><xref:System.Windows.Window> implements those behaviors and, consequently, you use <xref:System.Windows.Window> to create custom modal and modeless dialog boxes.</span></span>  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>
### <a name="creating-a-modal-custom-dialog-box"></a><span data-ttu-id="0082d-165">建立模式自訂對話方塊</span><span class="sxs-lookup"><span data-stu-id="0082d-165">Creating a modal custom dialog box</span></span>

<span data-ttu-id="0082d-166">本主題說明如何使用 <xref:System.Windows.Window> 來建立典型的強制回應對話方塊實 `Margins` 作為範例（請參閱[對話方塊範例](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)）。</span><span class="sxs-lookup"><span data-stu-id="0082d-166">This topic shows how to use <xref:System.Windows.Window> to create a typical modal dialog box implementation, using the `Margins` dialog box as an example (see [Dialog Box Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)).</span></span> <span data-ttu-id="0082d-167">`Margins`下圖顯示此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0082d-167">The `Margins` dialog box is shown in the following figure.</span></span>  
  
 ![[邊界] 對話方塊，其中包含用來定義左邊界、上邊界、右邊界和下邊界的欄位。](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a><span data-ttu-id="0082d-169">設定強制回應對話方塊</span><span class="sxs-lookup"><span data-stu-id="0082d-169">Configuring a modal dialog box</span></span>

<span data-ttu-id="0082d-170">一般對話方塊的使用者介面包括：</span><span class="sxs-lookup"><span data-stu-id="0082d-170">The user interface for a typical dialog box includes the following:</span></span>  
  
- <span data-ttu-id="0082d-171">收集想要的資料所需的各種控制項。</span><span class="sxs-lookup"><span data-stu-id="0082d-171">The various controls that are required to gather the desired data.</span></span>  
  
- <span data-ttu-id="0082d-172">使用者按一下 **[確定**] 按鈕以關閉對話方塊，並返回函式，然後繼續處理。</span><span class="sxs-lookup"><span data-stu-id="0082d-172">An **OK** button that users click to close the dialog box, return to the function, and continue processing.</span></span>  
  
- <span data-ttu-id="0082d-173">[**取消**] 按鈕，使用者可以按一下以關閉對話方塊，並停止函式進行進一步的處理。</span><span class="sxs-lookup"><span data-stu-id="0082d-173">A **Cancel** button that users click to close the dialog box and stop the function from further processing.</span></span>  
  
- <span data-ttu-id="0082d-174">標題列中的 [**關閉**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0082d-174">A **Close** button in the title bar.</span></span>  
  
- <span data-ttu-id="0082d-175">圖示。</span><span class="sxs-lookup"><span data-stu-id="0082d-175">An icon.</span></span>  
  
- <span data-ttu-id="0082d-176">**最小化**、**最大化**和**還原**按鈕。</span><span class="sxs-lookup"><span data-stu-id="0082d-176">**Minimize**, **Maximize**, and **Restore** buttons.</span></span>  
  
- <span data-ttu-id="0082d-177">用來最小化、最大化、還原和關閉對話方塊的**系統**功能表。</span><span class="sxs-lookup"><span data-stu-id="0082d-177">A **System** menu to minimize, maximize, restore, and close the dialog box.</span></span>  
  
- <span data-ttu-id="0082d-178">在開啟對話方塊之視窗的上方和中央位置。</span><span class="sxs-lookup"><span data-stu-id="0082d-178">A position above and in the center of the window that opened the dialog box.</span></span>  
  
- <span data-ttu-id="0082d-179">能夠在可能的情況下調整大小，讓對話方塊無法變得太小，並為使用者提供實用的預設大小。</span><span class="sxs-lookup"><span data-stu-id="0082d-179">The ability to be resized where possible to prevent the dialog box from being too small, and to provide the user with a useful default size.</span></span> <span data-ttu-id="0082d-180">這需要您設定預設值和最小維度。</span><span class="sxs-lookup"><span data-stu-id="0082d-180">This requires that you set both the default and a minimum dimensions.</span></span>  
  
- <span data-ttu-id="0082d-181">ESC 鍵，做為鍵盤快速鍵，可讓您按下 [**取消**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0082d-181">The ESC key as a keyboard shortcut that causes the **Cancel** button to be pressed.</span></span> <span data-ttu-id="0082d-182">方法是將 <xref:System.Windows.Controls.Button.IsCancel%2A> [**取消**] 按鈕的屬性設為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="0082d-182">You do this by setting the <xref:System.Windows.Controls.Button.IsCancel%2A> property of the **Cancel** button to `true`.</span></span>  
  
- <span data-ttu-id="0082d-183">輸入（或傳回）鍵做為鍵盤快速鍵，可讓您按下 [**確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0082d-183">The ENTER (or RETURN) key as a keyboard shortcut that causes the **OK** button to be pressed.</span></span> <span data-ttu-id="0082d-184">您可以藉由設定 [ <xref:System.Windows.Controls.Button.IsDefault%2A> **確定]** 按鈕的屬性來執行此動作 `true` 。</span><span class="sxs-lookup"><span data-stu-id="0082d-184">You do this by setting the <xref:System.Windows.Controls.Button.IsDefault%2A> property of the **OK** button `true`.</span></span>  
  
<span data-ttu-id="0082d-185">下列程式碼示範這項設定。</span><span class="sxs-lookup"><span data-stu-id="0082d-185">The following code demonstrates this configuration.</span></span>  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
<span data-ttu-id="0082d-186">對話方塊的使用者體驗也會延伸至開啟對話方塊之視窗的功能表列。</span><span class="sxs-lookup"><span data-stu-id="0082d-186">The user experience for a dialog box also extends into the menu bar of the window that opens the dialog box.</span></span> <span data-ttu-id="0082d-187">當功能表項目所執行的函式需要透過對話方塊進行使用者互動才能繼續時，該函式的功能表項目會在其標頭中顯示省略符號，如下所示。</span><span class="sxs-lookup"><span data-stu-id="0082d-187">When a menu item runs a function that requires user interaction through a dialog box before the function can continue, the menu item for the function will have an ellipsis in its header, as shown here.</span></span>  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
<span data-ttu-id="0082d-188">當功能表項目所執行的函式顯示不需要使用者互動的對話方塊時 (例如 [關於] 對話方塊)，則不需要省略符號。</span><span class="sxs-lookup"><span data-stu-id="0082d-188">When a menu item runs a function that displays a dialog box which does not require user interaction, such as an About dialog box, an ellipsis is not required.</span></span>  
  
#### <a name="opening-a-modal-dialog-box"></a><span data-ttu-id="0082d-189">開啟強制回應對話方塊</span><span class="sxs-lookup"><span data-stu-id="0082d-189">Opening a modal dialog box</span></span>

<span data-ttu-id="0082d-190">對話方塊通常是使用者選取功能表項目以執行定義域專屬函式所顯示的結果，例如在文書處理器中設定文件的邊界。</span><span class="sxs-lookup"><span data-stu-id="0082d-190">A dialog box is typically shown as a result of a user selecting a menu item to perform a domain-specific function, such as setting the margins of a document in a word processor.</span></span> <span data-ttu-id="0082d-191">將視窗顯示為對話方塊類似於顯示標準視窗，不過需要進行額外的對話方塊專屬設定。</span><span class="sxs-lookup"><span data-stu-id="0082d-191">Showing a window as a dialog box is similar to showing a normal window, although it requires additional dialog box-specific configuration.</span></span> <span data-ttu-id="0082d-192">具現化、設定及開啟對話方塊的整個過程如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="0082d-192">The entire process of instantiating, configuring, and opening a dialog box is shown in the following code.</span></span>  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

<span data-ttu-id="0082d-193">在這裡，此程式碼會將預設資訊（目前的邊界）傳遞至對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0082d-193">Here, the code passes default information (the current margins) to the dialog box.</span></span> <span data-ttu-id="0082d-194">它也會 <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> 使用顯示對話方塊之視窗的參考來設定屬性。</span><span class="sxs-lookup"><span data-stu-id="0082d-194">It also sets the <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> property with a reference to the window that is showing the dialog box.</span></span> <span data-ttu-id="0082d-195">一般來說，您應該一律設定對話方塊的 [擁有者]，提供所有對話方塊通用的視窗狀態相關行為（如需詳細資訊，請參閱[WPF Windows 總覽](wpf-windows-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="0082d-195">In general, you should always set the owner for a dialog box to provide window state-related behaviors that are common to all dialog boxes (see [WPF Windows Overview](wpf-windows-overview.md) for more information).</span></span>

> [!NOTE]
> <span data-ttu-id="0082d-196">您必須提供擁有者，以支援對話方塊的使用者介面（UI）自動化（請參閱[UI 自動化總覽](../../ui-automation/ui-automation-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="0082d-196">You must provide an owner to support user interface (UI) automation for dialog boxes (see [UI Automation Overview](../../ui-automation/ui-automation-overview.md)).</span></span>

<span data-ttu-id="0082d-197">設定對話方塊之後，會藉由呼叫方法來以模式顯示 <xref:System.Windows.Window.ShowDialog%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0082d-197">After the dialog box is configured, it is shown modally by calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span>  
  
#### <a name="validating-user-provided-data"></a><span data-ttu-id="0082d-198">驗證使用者提供的資料</span><span class="sxs-lookup"><span data-stu-id="0082d-198">Validating user-provided data</span></span>

<span data-ttu-id="0082d-199">在開啟對話方塊且使用者提供所需資料之後，對話方塊會基於下列原因負責確保提供的資料有效：</span><span class="sxs-lookup"><span data-stu-id="0082d-199">When a dialog box is opened and the user provides the required data, a dialog box is responsible for ensuring that the provided data is valid for the following reasons:</span></span>  
  
- <span data-ttu-id="0082d-200">從安全性的觀點來看，應該驗證所有輸入。</span><span class="sxs-lookup"><span data-stu-id="0082d-200">From a security perspective, all input should be validated.</span></span>  
  
- <span data-ttu-id="0082d-201">從定義域專屬的觀點來看，資料驗證可以防止程式碼處理錯誤的資料，這可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0082d-201">From a domain-specific perspective, data validation prevents erroneous data from being processed by the code, which could potentially throw exceptions.</span></span>  
  
- <span data-ttu-id="0082d-202">從使用者體驗的觀點來看，對話方塊可藉由對使用者顯示哪些輸入的資料無效來協助使用者。</span><span class="sxs-lookup"><span data-stu-id="0082d-202">From a user-experience perspective, a dialog box can help users by showing them which data they have entered is invalid.</span></span>  
  
- <span data-ttu-id="0082d-203">從效能的觀點來看，多層式應用程式中的資料驗證可以減少用戶層與應用程式層之間的來回行程次數，特別是當應用程式是由 Web 服務或伺服器架構資料庫組成時。</span><span class="sxs-lookup"><span data-stu-id="0082d-203">From a performance perspective, data validation in a multi-tier application can reduce the number of round trips between the client and the application tiers, particularly when the application is composed of Web services or server-based databases.</span></span>  

<span data-ttu-id="0082d-204">若要在 WPF 中驗證繫結控制項，您必須定義驗證規則，並將它與系結產生關聯。</span><span class="sxs-lookup"><span data-stu-id="0082d-204">To validate a bound control in WPF, you need to define a validation rule and associate it with the binding.</span></span> <span data-ttu-id="0082d-205">驗證規則是衍生自的自訂類別 <xref:System.Windows.Controls.ValidationRule> 。</span><span class="sxs-lookup"><span data-stu-id="0082d-205">A validation rule is a custom class that derives from <xref:System.Windows.Controls.ValidationRule>.</span></span> <span data-ttu-id="0082d-206">下列範例顯示驗證規則， `MarginValidationRule` 它會檢查系結的值是否為 <xref:System.Double> ，而且是否在指定的範圍內。</span><span class="sxs-lookup"><span data-stu-id="0082d-206">The following example shows a validation rule, `MarginValidationRule`, which checks that a bound value is a <xref:System.Double> and is within a specified range.</span></span>  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

<span data-ttu-id="0082d-207">在此程式碼中，驗證規則的驗證邏輯是藉由覆寫 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法來執行，它會驗證資料並傳回適當的 <xref:System.Windows.Controls.ValidationResult> 。</span><span class="sxs-lookup"><span data-stu-id="0082d-207">In this code, the validation logic of a validation rule is implemented by overriding the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method, which validates the data and returns an appropriate <xref:System.Windows.Controls.ValidationResult>.</span></span>  

<span data-ttu-id="0082d-208">若要建立驗證規則與繫結控制項的關聯，您可以使用下列標記。</span><span class="sxs-lookup"><span data-stu-id="0082d-208">To associate the validation rule with the bound control, you use the following markup.</span></span>  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

<span data-ttu-id="0082d-209">一旦與驗證規則相關聯，WPF 會在將資料輸入繫結控制項時自動套用。</span><span class="sxs-lookup"><span data-stu-id="0082d-209">Once the validation rule is associated, WPF will automatically apply it when data is entered into the bound control.</span></span> <span data-ttu-id="0082d-210">當控制項包含不正確資料時，WPF 會在不正確控制項周圍顯示紅色框線，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="0082d-210">When a control contains invalid data, WPF will display a red border around the invalid control, as shown in the following figure.</span></span>  
  
![邊界對話方塊，在不正確左邊界值周圍有紅色框線。](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

<span data-ttu-id="0082d-212">WPF 在輸入有效的資料之前，不會將使用者限制為不正確控制項。</span><span class="sxs-lookup"><span data-stu-id="0082d-212">WPF does not restrict a user to the invalid control until they have entered valid data.</span></span> <span data-ttu-id="0082d-213">這是很好的對話方塊行為；使用者應該能夠自由地巡覽對話方塊中的控制項，而不論資料是否有效。</span><span class="sxs-lookup"><span data-stu-id="0082d-213">This is good behavior for a dialog box; a user should be able to freely navigate the controls in a dialog box whether or not data is valid.</span></span> <span data-ttu-id="0082d-214">不過，這表示使用者可以輸入不正確資料，然後按下 [**確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0082d-214">However, this means a user can enter invalid data and press the **OK** button.</span></span> <span data-ttu-id="0082d-215">基於這個理由，您的程式碼也需要在處理事件時按下 [**確定**] 按鈕時，驗證對話方塊中的所有控制項 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 。</span><span class="sxs-lookup"><span data-stu-id="0082d-215">For this reason, your code also needs to validate all controls in a dialog box when the **OK** button is pressed by handling the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

<span data-ttu-id="0082d-216">這個程式碼會列舉視窗上的所有相依性物件，如果有任何不正確（如所傳回），則 <xref:System.Windows.Controls.Validation.GetHasError%2A> 不正確控制項會取得焦點， `IsValid` 方法 `false` 會傳回，而此視窗會被視為無效。</span><span class="sxs-lookup"><span data-stu-id="0082d-216">This code enumerates all dependency objects on a window and, if any are invalid (as returned by <xref:System.Windows.Controls.Validation.GetHasError%2A>, the invalid control gets the focus, the `IsValid` method returns `false`, and the window is considered invalid.</span></span>  
  
<span data-ttu-id="0082d-217">一旦對話方塊有效，就可以安全地將它關閉並傳回。</span><span class="sxs-lookup"><span data-stu-id="0082d-217">Once a dialog box is valid, it can safely close and return.</span></span> <span data-ttu-id="0082d-218">在傳回過程中，必須將結果傳回呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="0082d-218">As part of the return process, it needs to return a result to the calling function.</span></span>  
  
#### <a name="setting-the-modal-dialog-result"></a><span data-ttu-id="0082d-219">設定強制回應對話方塊結果</span><span class="sxs-lookup"><span data-stu-id="0082d-219">Setting the modal dialog result</span></span>

<span data-ttu-id="0082d-220">使用開啟對話方塊 <xref:System.Windows.Window.ShowDialog%2A> ，基本上就像呼叫方法一樣：使用開啟對話方塊的程式碼會等候， <xref:System.Windows.Window.ShowDialog%2A> 直到傳回為止 <xref:System.Windows.Window.ShowDialog%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0082d-220">Opening a dialog box using <xref:System.Windows.Window.ShowDialog%2A> is fundamentally like calling a method: the code that opened the dialog box using <xref:System.Windows.Window.ShowDialog%2A> waits until <xref:System.Windows.Window.ShowDialog%2A> returns.</span></span> <span data-ttu-id="0082d-221">當傳回時 <xref:System.Windows.Window.ShowDialog%2A> ，呼叫它的程式碼必須根據使用者是否按下 [**確定]** 按鈕或 [**取消**] 按鈕，決定是否要繼續處理或停止處理。</span><span class="sxs-lookup"><span data-stu-id="0082d-221">When <xref:System.Windows.Window.ShowDialog%2A> returns, the code that called it needs to decide whether to continue processing or stop processing, based on whether the user pressed the **OK** button or the **Cancel** button.</span></span> <span data-ttu-id="0082d-222">為了協助進行這種決策，對話方塊必須傳回使用者的選擇，做為 <xref:System.Boolean> 從方法傳回的值 <xref:System.Windows.Window.ShowDialog%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0082d-222">To facilitate this decision, the dialog box needs to return the user's choice as a <xref:System.Boolean> value that is returned from the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span>  

<span data-ttu-id="0082d-223">按一下 [**確定]** 按鈕時， <xref:System.Windows.Window.ShowDialog%2A> 應該會傳回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="0082d-223">When the **OK** button is clicked, <xref:System.Windows.Window.ShowDialog%2A> should return `true`.</span></span> <span data-ttu-id="0082d-224"><xref:System.Windows.Window.DialogResult%2A>當按一下 [**確定]** 按鈕時，設定對話方塊的屬性即可達成此目的。</span><span class="sxs-lookup"><span data-stu-id="0082d-224">This is achieved by setting the <xref:System.Windows.Window.DialogResult%2A> property of the dialog box when the **OK** button is clicked.</span></span>  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

<span data-ttu-id="0082d-225">請注意，設定 <xref:System.Windows.Window.DialogResult%2A> 屬性也會使視窗自動關閉，這可減輕明確呼叫的需求 <xref:System.Windows.Window.Close%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0082d-225">Note that setting the <xref:System.Windows.Window.DialogResult%2A> property also causes the window to close automatically, which alleviates the need to explicitly call <xref:System.Windows.Window.Close%2A>.</span></span>  
  
<span data-ttu-id="0082d-226">按一下 [**取消**] 按鈕時， <xref:System.Windows.Window.ShowDialog%2A> 應該會傳回 `false` ，這也需要設定 <xref:System.Windows.Window.DialogResult%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="0082d-226">When the **Cancel** button is clicked, <xref:System.Windows.Window.ShowDialog%2A> should return `false`, which also requires setting the <xref:System.Windows.Window.DialogResult%2A> property.</span></span>  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

<span data-ttu-id="0082d-227">當按鈕的 <xref:System.Windows.Controls.Button.IsCancel%2A> 屬性設定為 `true` ，而且使用者按下 [**取消**] 按鈕或 ESC 鍵時，會 <xref:System.Windows.Window.DialogResult%2A> 自動設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="0082d-227">When a button's <xref:System.Windows.Controls.Button.IsCancel%2A> property is set to `true` and the user presses either the **Cancel** button or the ESC key, <xref:System.Windows.Window.DialogResult%2A> is automatically set to `false`.</span></span> <span data-ttu-id="0082d-228">下列標記與上述程式碼具有相同的效果，而不需要處理 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="0082d-228">The following markup has the same effect as the preceding code, without the need to handle the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

<span data-ttu-id="0082d-229">`false`當使用者按下標題列中的 [**關閉**] 按鈕，或從 [**系統**] 功能表選擇 [**關閉**] 功能表項目時，對話方塊就會自動返回。</span><span class="sxs-lookup"><span data-stu-id="0082d-229">A dialog box automatically returns `false` when a user presses the **Close** button in the title bar or chooses the **Close** menu item from the **System** menu.</span></span>  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a><span data-ttu-id="0082d-230">處理從強制回應對話方塊傳回的資料</span><span class="sxs-lookup"><span data-stu-id="0082d-230">Processing data returned from a modal dialog box</span></span>  

<span data-ttu-id="0082d-231">當 <xref:System.Windows.Window.DialogResult%2A> 由對話方塊設定時，開啟它的函式可以在傳回時檢查屬性，以取得對話方塊的結果 <xref:System.Windows.Window.DialogResult%2A> <xref:System.Windows.Window.ShowDialog%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0082d-231">When <xref:System.Windows.Window.DialogResult%2A> is set by a dialog box, the function that opened it can get the dialog box result by inspecting the <xref:System.Windows.Window.DialogResult%2A> property when <xref:System.Windows.Window.ShowDialog%2A> returns.</span></span>  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

<span data-ttu-id="0082d-232">如果對話方塊結果為，則函式會 `true` 使用該函式做為提示，以取得並處理使用者所提供的資料。</span><span class="sxs-lookup"><span data-stu-id="0082d-232">If the dialog result is `true`, the function uses that as a cue to retrieve and process the data provided by the user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0082d-233"><xref:System.Windows.Window.ShowDialog%2A>傳回之後，就無法重新開啟對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0082d-233">After <xref:System.Windows.Window.ShowDialog%2A> has returned, a dialog box cannot be reopened.</span></span> <span data-ttu-id="0082d-234">您必須改為建立新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0082d-234">Instead, you need to create a new instance.</span></span>

<span data-ttu-id="0082d-235">如果對話方塊結果為 `false` ，函數應該會適當地結束處理。</span><span class="sxs-lookup"><span data-stu-id="0082d-235">If the dialog result is `false`, the function should end processing appropriately.</span></span>  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>
### <a name="creating-a-modeless-custom-dialog-box"></a><span data-ttu-id="0082d-236">建立非模式自訂對話方塊</span><span class="sxs-lookup"><span data-stu-id="0082d-236">Creating a modeless custom dialog box</span></span>

<span data-ttu-id="0082d-237">非強制回應對話方塊 (例如下圖所示的 [尋找] 對話方塊) 與強制回應對話方塊具有相同的基本外觀。</span><span class="sxs-lookup"><span data-stu-id="0082d-237">A modeless dialog box, such as the Find Dialog Box shown in the following figure, has the same fundamental appearance as the modal dialog box.</span></span>  

![顯示 [尋找] 對話方塊的螢幕擷取畫面。](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

<span data-ttu-id="0082d-239">不過，其行為稍有不同，如下列各節中所述。</span><span class="sxs-lookup"><span data-stu-id="0082d-239">However, the behavior is slightly different, as described in the following sections.</span></span>  
  
#### <a name="opening-a-modeless-dialog-box"></a><span data-ttu-id="0082d-240">開啟非強制回應對話方塊</span><span class="sxs-lookup"><span data-stu-id="0082d-240">Opening a modeless dialog box</span></span>

<span data-ttu-id="0082d-241">藉由呼叫方法，即可開啟非強制回應對話方塊 <xref:System.Windows.Window.Show%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0082d-241">A modeless dialog box is opened by calling the <xref:System.Windows.Window.Show%2A> method.</span></span>  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  

[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

<span data-ttu-id="0082d-242">不同于 <xref:System.Windows.Window.ShowDialog%2A> ，會 <xref:System.Windows.Window.Show%2A> 立即傳回。</span><span class="sxs-lookup"><span data-stu-id="0082d-242">Unlike <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> returns immediately.</span></span> <span data-ttu-id="0082d-243">因此，呼叫視窗無法得知非強制回應對話方塊何時關閉，因此不會知道何時要檢查對話方塊結果，或從對話方塊取得資料以進一步處理。</span><span class="sxs-lookup"><span data-stu-id="0082d-243">Consequently, the calling window cannot tell when the modeless dialog box is closed and, therefore, does not know when to check for a dialog box result or get data from the dialog box for further processing.</span></span> <span data-ttu-id="0082d-244">相反地，對話方塊必須建立其他方式，以將資料傳回呼叫視窗進行處理。</span><span class="sxs-lookup"><span data-stu-id="0082d-244">Instead, the dialog box needs to create an alternative way to return data to the calling window for processing.</span></span>  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a><span data-ttu-id="0082d-245">處理從非強制回應對話方塊傳回的資料</span><span class="sxs-lookup"><span data-stu-id="0082d-245">Processing data returned from a modeless dialog box</span></span>  

<span data-ttu-id="0082d-246">在此範例中， `FindDialogBox` 可能會將一或多個尋找結果傳回主視窗，視搜尋的文字沒有任何特定頻率而定。</span><span class="sxs-lookup"><span data-stu-id="0082d-246">In this example, the `FindDialogBox` may return one or more find results to the main window, depending on the text being searched for without any specific frequency.</span></span> <span data-ttu-id="0082d-247">如同強制回應對話方塊，非強制回應對話方塊可以透過屬性傳回結果。</span><span class="sxs-lookup"><span data-stu-id="0082d-247">As with a modal dialog box, a modeless dialog box can return results using properties.</span></span> <span data-ttu-id="0082d-248">不過，主控對話方塊的視窗必須知道何時要查看這些屬性。</span><span class="sxs-lookup"><span data-stu-id="0082d-248">However, the window that owns the dialog box needs to know when to check those properties.</span></span> <span data-ttu-id="0082d-249">其中一個做法是，讓對話方塊實作每次找到文字時所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="0082d-249">One way to enable this is for the dialog box to implement an event that is raised whenever text is found.</span></span> <span data-ttu-id="0082d-250">`FindDialogBox``TextFoundEvent`針對此目的執行，這會先需要委派。</span><span class="sxs-lookup"><span data-stu-id="0082d-250">`FindDialogBox` implements the `TextFoundEvent` for this purpose, which first requires a delegate.</span></span>  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

<span data-ttu-id="0082d-251">使用委派時，會執行 `TextFoundEventHandler` `FindDialogBox` `TextFoundEvent` 。</span><span class="sxs-lookup"><span data-stu-id="0082d-251">Using the `TextFoundEventHandler` delegate, `FindDialogBox` implements the `TextFoundEvent`.</span></span>
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

<span data-ttu-id="0082d-252">因此， `Find` 可以在找到搜尋結果時引發事件。</span><span class="sxs-lookup"><span data-stu-id="0082d-252">Consequently, `Find` can raise the event when a search result is found.</span></span>  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

<span data-ttu-id="0082d-253">主控視窗接著需要註冊及處理此事件。</span><span class="sxs-lookup"><span data-stu-id="0082d-253">The owner window then needs to register with and handle this event.</span></span>

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a><span data-ttu-id="0082d-254">關閉非強制回應對話方塊</span><span class="sxs-lookup"><span data-stu-id="0082d-254">Closing a modeless dialog box</span></span>

<span data-ttu-id="0082d-255">因為 <xref:System.Windows.Window.DialogResult%2A> 不需要設定，所以您可以使用系統提供的機制來關閉非強制回應對話方塊，包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="0082d-255">Because <xref:System.Windows.Window.DialogResult%2A> does not need to be set, a modeless dialog can be closed using system provide mechanisms, including the following:</span></span>  
  
- <span data-ttu-id="0082d-256">按一下標題列中的 [**關閉**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0082d-256">Clicking the **Close** button in the title bar.</span></span>  
  
- <span data-ttu-id="0082d-257">按下 ALT+F4。</span><span class="sxs-lookup"><span data-stu-id="0082d-257">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="0082d-258">從 [**系統**] 功能表選擇 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="0082d-258">Choosing **Close** from the **System** menu.</span></span>  
  
<span data-ttu-id="0082d-259">或者， <xref:System.Windows.Window.Close%2A> 當您按一下 [**關閉**] 按鈕時，您的程式碼可以呼叫。</span><span class="sxs-lookup"><span data-stu-id="0082d-259">Alternatively, your code can call <xref:System.Windows.Window.Close%2A> when the **Close** button is clicked.</span></span>  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a><span data-ttu-id="0082d-260">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0082d-260">See also</span></span>

- [<span data-ttu-id="0082d-261">快顯功能表概觀</span><span class="sxs-lookup"><span data-stu-id="0082d-261">Popup Overview</span></span>](../controls/popup-overview.md)
- [<span data-ttu-id="0082d-262">Dialog Box Sample (對話方塊範例)</span><span class="sxs-lookup"><span data-stu-id="0082d-262">Dialog Box Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)
