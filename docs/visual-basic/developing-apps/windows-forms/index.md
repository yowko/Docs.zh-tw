---
title: Windows Forms 應用程式基本概念 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: b900b85b4e3e56dbc587a15edea40f6e3032cbd1
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521677"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Windows Forms 應用程式基本概念 (Visual Basic)
Visual Basic 中很重要的一部分是建立本機使用者的電腦執行的 Windows Forms 應用程式的能力。 您可以使用 Visual Studio 來建立使用 Windows Form 的應用程式和使用者介面。 在 Windows Forms 應用程式的基礎類別<xref:System.Windows.Forms>命名空間。  
  
## <a name="designing-windows-forms-applications"></a>設計 Windows Forms 應用程式  
 您可以使用 Visual Studio 建立 Windows Form 和 Windows 服務應用程式。 如需詳細資訊，請參閱下列主題：  
  
-   [開始使用 Windows Form](../../../framework/winforms/getting-started-with-windows-forms.md)。 提供有關如何建立和撰寫 Windows Forms 的資訊。  
   
-   [Windows Form 控制項](../../../framework/winforms/controls/index.md)。 主題詳細說明使用 Windows Form 控制項的集合。  
  
-   [Windows 服務應用程式](../../../framework/windows-services/index.md)。 列出主題，說明如何建立 Windows 服務。  
  
## <a name="building-rich-interactive-user-interfaces"></a>建置豐富、互動式的使用者介面  
 Windows Form 是智慧型用戶端元件[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]，一組 managed 程式庫可讓一般的應用程式工作，例如讀取和寫入至檔案系統。 使用像是 Visual Studio 的開發環境，您可以建立 Windows Form 應用程式來顯示資訊、 要求使用者，輸入，並進行通訊與遠端電腦透過網路。  
  
 在 Windows Forms 中，表單是一種視覺化介面，在上面顯示的資訊給使用者。 通常，您會建置 Windows Form 應用程式將放在表單上的控制項，並開發回應使用者動作，例如滑鼠點按或是按鍵動作。 「控制項」是獨立的使用者介面 (UI) 項目，可顯示資料或接受資料輸入。  
  
### <a name="events"></a>事件  
 當使用者執行某個動作，您的表單或其中一個控制項時，它會產生事件。 您的應用程式會使用程式碼對這些事件做出反應，並且在事件發生時加以處理。 如需詳細資訊，請參閱[在 Windows Forms 中建立事件處理常式](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)。  
  
### <a name="controls"></a>控制項  
 Windows Form 包含各種可以放在表單的控制項： 顯示文字方塊、 按鈕、 下拉式清單方塊、 選項按鈕和甚至還有網頁控制項。 如需您可以在表單上使用之所有控制項的清單，請參閱[要在 Windows Forms 上使用的控制項](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md)。 如果現有的控制項不符合您的需求，Windows Form 也支援使用 <xref:System.Windows.Forms.UserControl> 類別來建立您自己的自訂控制項。  
  
 Windows Form 有豐富的 UI 控制項，可以模擬高階應用程式 (例如 Microsoft Office) 中的功能。 使用<xref:System.Windows.Forms.ToolStrip>和<xref:System.Windows.Forms.MenuStrip>控制項，您可以建立工具列和功能表，包含文字和影像，顯示子功能表，以及裝載其他控制項，例如文字方塊和下拉式方塊。  
  
 使用 Visual Studio 拖放表單設計工具中，您可以輕鬆地建立 Windows Forms 應用程式： 只要選取游標的控制項，並將它們放您想要用在表單上。 設計工具提供工具，例如格線與 「 對齊線 」 以讓您輕鬆對齊控制項。 無論您使用 Visual Studio，或在命令列進行編譯，您可以使用<xref:System.Windows.Forms.FlowLayoutPanel>，<xref:System.Windows.Forms.TableLayoutPanel>和<xref:System.Windows.Forms.SplitContainer>控制項來建立進階表單配置的最少的時間和精力。  
  
### <a name="custom-ui-elements"></a>自訂 UI 項目  
 最後，如果您必須建立您自己自訂的 UI 項目，<xref:System.Drawing>命名空間包含所有您要呈現線條、 圓形和其他圖形，直接在表單上的類別。  
  
 如需使用這些功能的逐步資訊，請參閱下列說明主題。  
  
|以|請參閱|  
|--------|---------|  
|使用 Visual Studio 中建立新的 Windows Forms 應用程式|[逐步解說： 建立簡單 Windows Form](https://msdn.microsoft.com/library/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|使用在表單上控制項|[操作說明：將控制項新增至 Windows Forms](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|   
|建立使用圖形 <xref:System.Drawing>|[圖形程式設計入門](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|建立自訂控制項|[操作說明：繼承自 UserControl 類別](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
## <a name="displaying-and-manipulating-data"></a>顯示和操作資料  
 許多應用程式必須顯示來自資料庫、XML 檔案、XML Web 服務或其他資料來源的資料。 Windows Form 提供彈性的控制項稱為<xref:System.Windows.Forms.DataGridView>呈現傳統資料列和資料行格式，這類表格式資料，使每一項資料佔有自己的儲存格的控制項。 使用<xref:System.Windows.Forms.DataGridView>您可以自訂個別儲存格的外觀、 鎖定任意的資料列和資料行就位，並顯示在儲存格中，至於其他功能的複雜控制項。  
  
 利用 Windows Form 智慧型用戶端，透過網路連接到資料來源是一項簡單的工作。 <xref:System.Windows.Forms.BindingSource> 元件 (Windows Form 在 [!INCLUDE[vsprvslong](~/includes/vsprvslong-md.md)] 和 [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] 中的新元件) 提供連線至資料來源，並公開將資料繫結至控制項的方法：巡覽至上一筆和下一筆記錄、編輯記錄，以及將變更儲存回原始來源。 <xref:System.Windows.Forms.BindingNavigator> 控制項透過 <xref:System.Windows.Forms.BindingSource> 元件提供一個簡單的介面，可讓使用者在記錄之間巡覽。  
  
### <a name="data-bound-controls"></a>資料繫結控制項  
 您可以建立資料繫結控制項輕鬆地使用資料來源視窗中，顯示您的專案中的資料來源，例如資料庫、 Web 服務和物件。 將項目從這個視窗拖曳到專案中的表單上，即可建立資料繫結控制項。 您也可以將物件從 [資料來源] 視窗拖曳至現有的控制項，以將現有的控制項繫結至資料。  
  
### <a name="settings"></a>設定  
 您可以管理在 Windows Form 中的資料繫結的另一種是設定。 大部分的智慧型用戶端應用程式必須保留其執行階段狀態，例如表單最後已知大小的一些資訊，並保留使用者喜好設定資料，例如儲存檔案的預設位置。 應用程式設定功能會提供簡單的方式來儲存這兩種設定用戶端電腦上，以處理這些需求。 一旦定義使用 Visual Studio 或程式碼編輯器，這些設定會保存為 XML，並在執行階段自動讀回記憶體。  
  
 如需使用這些功能的逐步資訊，請參閱下列說明主題。  
  
|以|請參閱|  
|--------|---------|  
|使用<xref:System.Windows.Forms.BindingSource>元件|[操作說明：使用設計工具將 Windows Forms 控制項和 BindingSource 元件加以繫結](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|使用[!INCLUDE[vstecado](~/includes/vstecado-md.md)]資料來源|[操作說明：使用 Windows Forms BindingSource 元件排序和篩選 ADO.NET 資料](../../../framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|使用 [資料來源] 視窗|[逐步解說：顯示 Windows Form 上的資料](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>將應用程式部署到用戶端電腦  
 一旦您撰寫您的應用程式，您必須傳送給您的使用者，讓他們可以安裝並執行它自己的用戶端電腦上。 使用[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]技術，您可以使用按幾下即可部署您從 Visual Studio 內的應用程式和使用者提供指向您在網站上的應用程式的 URL。 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 會管理所有的項目和您的應用程式中的相依性，並確保應用程式已正確安裝用戶端電腦上。  
  
 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 應用程式可以設定為只在使用者連線到網路時執行，或是線上和離線時都可執行。 當您指定應用程式應該支援離線作業時，[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]將連結新增至您的應用程式在使用者的**啟動** 功能表，讓使用者可以不用透過 URL 開啟它。  
  
 當您更新應用程式時，您可以將新的部署資訊清單和新的應用程式複本發行到 Web 伺服器。 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 偵測到有可用的更新，並升級使用者的安裝;沒有自訂的程式設計，才能更新舊組件。  
  
 如需 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 的完整介紹，請參閱 [ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)。 如需使用這些功能的逐步資訊，請參閱下列說明主題：  
  
|以|請參閱|  
|--------|---------|  
|部署應用程式 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[如何：使用發行精靈發行 ClickOnce 應用程式](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [逐步解說：手動部署 ClickOnce 應用程式](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|更新[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]部署|[如何：管理 ClickOnce 應用程式的更新](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|管理與安全性 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[如何：啟用 ClickOnce 安全性設定](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>其他控制項和功能  
 Windows Form 中還有許多其他功能，可讓您快速、輕鬆地實作一般工作，例如支援建立對話方塊、列印、加入說明和文件，以及將您的應用程式當地語系化為多種語言。 此外，Windows Form 依賴強固的安全性系統[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]，讓您發行至您的客戶更安全的應用程式。  
  
 如需使用這些功能的逐步資訊，請參閱下列說明主題：  
  
|以|請參閱|  
|--------|---------|  
|列印表單的內容|[如何：列印 Windows Forms 中的圖形](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [如何：在 Windows Forms 中列印多頁文字檔](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|   
|深入了解 Windows Form 安全性|[Windows Forms 中的安全性概觀](../../../framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
- [Windows Forms 概觀](../../../framework/winforms/windows-forms-overview.md)  
- [My.Forms 物件](../../../visual-basic/language-reference/objects/my-forms-object.md)
