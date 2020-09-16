---
title: Windows Forms 應用程式基本概念
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: 9d061aeccb914cce80e02bb7df44dae2edf25412
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557015"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Windows Form 應用程式基本概念 (Visual Basic)

Visual Basic 的其中一個重要部分，就是能夠建立在使用者電腦本機上執行的 Windows Forms 應用程式。 您可以使用 Visual Studio，使用 Windows Forms 來建立應用程式和使用者介面。 Windows Forms 的應用程式是以命名空間中的類別為基礎 <xref:System.Windows.Forms> 。

## <a name="designing-windows-forms-applications"></a>設計 Windows Forms 應用程式

您可以使用 Visual Studio 來建立 Windows Forms 和 Windows 服務應用程式。 如需詳細資訊，請參閱下列主題：

- [消費者入門與 Windows Forms](/dotnet/desktop/winforms/getting-started-with-windows-forms)。 提供有關如何建立和程式 Windows Forms 的資訊。

- [Windows Forms 控制項](/dotnet/desktop/winforms/controls/)。 詳細說明如何使用 Windows Forms 控制項的主題集合。

- [Windows 服務應用程式](../../../framework/windows-services/index.md)。 列出說明如何建立 Windows 服務的主題。

## <a name="building-rich-interactive-user-interfaces"></a>建置豐富、互動式的使用者介面

Windows Forms 是 .NET Framework 的智慧型用戶端元件，這是一組 managed 程式庫，可啟用常見的應用程式工作，例如讀取和寫入檔案系統。 使用 Visual Studio 等開發環境時，您可以建立 Windows Forms 的應用程式，以顯示資訊、要求使用者輸入，以及透過網路與遠端電腦通訊。

在 Windows Form 中，「表單」(form) 是一種視覺化介面，您可以在上面顯示要提供給使用者的資訊。 您通常會將控制項放在表單上，並開發使用者動作的回應（例如滑鼠點按或按鍵按下），藉此建立 Windows Forms 應用程式。 「控制項」** 是獨立的使用者介面 (UI) 項目，可顯示資料或接受資料輸入。

### <a name="events"></a>事件

當使用者對您的表單或其中一個控制項執行某些工作時，會產生事件。 您的應用程式會使用程式碼對這些事件做出反應，並且在事件發生時加以處理。 如需詳細資訊，請參閱[在 Windows Forms 中建立事件處理常式](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms)。

### <a name="controls"></a>控制項

Windows Forms 包含各種可放置在表單上的控制項：顯示文字方塊、按鈕、下拉式方塊、選項按鈕，甚至是網頁的控制項。 如需您可以在表單上使用之所有控制項的清單，請參閱[要在 Windows Forms 上使用的控制項](/dotnet/desktop/winforms/controls/controls-to-use-on-windows-forms)。 如果現有的控制項不符合您的需求，Windows Form 也支援使用 <xref:System.Windows.Forms.UserControl> 類別來建立您自己的自訂控制項。

Windows Form 有豐富的 UI 控制項，可以模擬高階應用程式 (例如 Microsoft Office) 中的功能。 <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.MenuStrip> 您可以使用和控制項來建立包含文字和影像的工具列和功能表、顯示子功能表，以及裝載其他控制項（例如文字方塊和下拉式方塊）。

利用 Visual Studio 拖放表單設計工具，您可以輕鬆地建立 Windows Forms 應用程式：只要選取具有游標的控制項，並將它們放在表單上您想要的位置即可。 設計工具會提供格線和「對齊線」等工具來避免對齊控制項的麻煩。 無論您是在命令列使用 Visual Studio 或編譯，都可以使用 <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel> 和 <xref:System.Windows.Forms.SplitContainer> 控制項，以最短的時間和精力來建立先進的表單版面配置。

### <a name="custom-ui-elements"></a>自訂 UI 元素

最後，如果您必須建立自己的自訂 UI 元素，則 <xref:System.Drawing> 命名空間會包含您在表單上直接轉譯線條、圓形和其他圖形所需的所有類別。

如需使用這些功能的逐步解說資訊，請參閱下列說明主題。

|收件者|請參閱|
|--------|---------|
|使用 Visual Studio 建立新的 Windows Forms 應用程式|[教學課程1：建立圖片檢視器](/visualstudio/ide/tutorial-1-create-a-picture-viewer)|
|在表單上使用控制項|[如何：將控制項新增至 Windows Forms](/dotnet/desktop/winforms/controls/how-to-add-controls-to-windows-forms)|
|建立圖形 <xref:System.Drawing>|[圖形程式設計入門](/dotnet/desktop/winforms/advanced/getting-started-with-graphics-programming)|
|建立自訂控制項|[作法：繼承 UserControl 類別](/dotnet/desktop/winforms/controls/how-to-inherit-from-the-usercontrol-class)|

## <a name="displaying-and-manipulating-data"></a>顯示和操作資料

許多應用程式必須顯示來自資料庫、XML 檔案、XML Web 服務或其他資料來源的資料。 Windows Forms 提供了一個有彈性的控制項，稱為控制項，以 <xref:System.Windows.Forms.DataGridView> 傳統的資料列和資料行格式轉譯這類表格式資料，讓每個資料片段都佔用它自己的資料格。 <xref:System.Windows.Forms.DataGridView>您可以使用來自訂個別儲存格的外觀、就地鎖定任意的資料列和資料行，以及在資料格內顯示覆雜的控制項，還有其他功能。

利用 Windows Form 智慧型用戶端，透過網路連接到資料來源是一項簡單的工作。 <xref:System.Windows.Forms.BindingSource>Visual Studio 2005 和 .NET Framework 2.0 中 Windows Forms 的新元件代表與資料來源的連接，並公開將資料系結至控制項、流覽至上一筆和下一筆記錄、編輯記錄，以及將變更儲存回原始來源的方法。 <xref:System.Windows.Forms.BindingNavigator> 控制項透過 <xref:System.Windows.Forms.BindingSource> 元件提供一個簡單的介面，可讓使用者在記錄之間巡覽。

### <a name="data-bound-controls"></a>資料繫結控制項

您可以使用 [資料來源] 視窗輕鬆地建立資料繫結控制項，以顯示專案中的資料來源，例如資料庫、Web 服務和物件。 將項目從這個視窗拖曳到專案中的表單上，即可建立資料繫結控制項。 您也可以將物件從 [資料來源] 視窗拖曳至現有的控制項，以將現有的控制項繫結至資料。

### <a name="settings"></a>設定

在 Windows Form 中，另一種管理資料繫結的方法是「設定」(settings)。 大部分的智慧型用戶端應用程式都必須保留一些有關執行時間狀態的資訊，例如最後已知的表單大小，以及保留使用者喜好設定資料（例如儲存檔案的預設位置）。 應用程式設定功能可讓您輕鬆地在用戶端電腦上儲存這兩種類型的設定，以解決這些需求。 一旦使用 Visual Studio 或程式碼編輯器定義之後，這些設定會保存為 XML，並在執行時間自動讀取回記憶體。

如需使用這些功能的逐步解說資訊，請參閱下列說明主題。

|收件者|請參閱|
|--------|---------|
|使用 <xref:System.Windows.Forms.BindingSource> 元件|[作法：使用設計工具繫結 Windows Forms 控制項和 BindingSource 元件](/dotnet/desktop/winforms/controls/bind-wf-controls-with-the-bindingsource)|
|使用 ADO.NET 資料來源|[作法：使用 Windows Forms BindingSource 元件排序和篩選 ADO.NET 資料](/dotnet/desktop/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component)|
|使用 [資料來源] 視窗|[逐步解說：顯示 Windows Form 上的資料](/visualstudio/data-tools/accessing-data-in-visual-studio)|

## <a name="deploying-applications-to-client-computers"></a>將應用程式部署到用戶端電腦

撰寫您的應用程式之後，您必須將它傳送給您的使用者，讓他們可以在自己的用戶端電腦上安裝和執行應用程式。 使用 ClickOnce 技術，您只要按幾下滑鼠，就可以從 Visual Studio 內部署應用程式，並為使用者提供指向 Web 上應用程式的 URL。 ClickOnce 會管理應用程式中的所有元素和相依性，並確保應用程式已正確安裝在用戶端電腦上。

ClickOnce 應用程式可以設定為只有在使用者連線到網路時才執行，或是在線上和離線時執行。 當您指定應用程式應該支援離線作業時，ClickOnce 會在使用者的 [ **開始** ] 功能表中新增應用程式的連結，讓使用者可以在不使用 URL 的情況下開啟該應用程式。

當您更新應用程式時，您可以將新的部署資訊清單和新的應用程式複本發行到 Web 伺服器。 ClickOnce 偵測到有可用的更新，並升級使用者的安裝;不需要自訂程式設計就能更新舊的元件。

如需 ClickOnce 的完整簡介，請參閱 [Clickonce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)。 如需使用這些功能的逐步解說資訊，請參閱下列說明主題：

|收件者|請參閱|
|--------|---------|
|使用 ClickOnce 部署應用程式|[如何：使用發佈嚮導發行 ClickOnce 應用程式](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [逐步解說：手動部署 ClickOnce 應用程式](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|
|更新 ClickOnce 部署|[如何：管理 ClickOnce 應用程式的更新](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|
|使用 ClickOnce 管理安全性|[如何：啟用 ClickOnce 安全性設定](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|

## <a name="other-controls-and-features"></a>其他控制項和功能

Windows Form 中還有許多其他功能，可讓您快速、輕鬆地實作一般工作，例如支援建立對話方塊、列印、加入說明和文件，以及將您的應用程式當地語系化為多種語言。 此外，Windows Forms 依賴 .NET Framework 的健全安全性系統，讓您可以將更安全的應用程式發行給客戶。

如需使用這些功能的逐步解說資訊，請參閱下列說明主題：

|收件者|請參閱|
|--------|---------|
|列印表單的內容|[作法：列印 Windows Forms 中的圖形](/dotnet/desktop/winforms/advanced/how-to-print-graphics-in-windows-forms)<br /><br /> [作法：在 Windows Forms 中列印多頁文字檔](/dotnet/desktop/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms)|
|深入了解 Windows Form 安全性|[Windows Form 中的安全性概觀](/dotnet/desktop/winforms/security-in-windows-forms-overview)|

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Windows Form 概觀](/dotnet/desktop/winforms/windows-forms-overview)
- [My.Forms 物件](../../language-reference/objects/my-forms-object.md)
