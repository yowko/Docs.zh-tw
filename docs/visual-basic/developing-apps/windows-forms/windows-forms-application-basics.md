---
title: "Windows Form 應用程式基本概念 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8275d3c06ebd89254a07127b4850d32ef0580830
ms.lasthandoff: 03/13/2017

---
# <a name="windows-forms-application-basics-visual-basic"></a>Windows Forms 應用程式基本概念 (Visual Basic)
很重要的一部分[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]是建立本機使用者的電腦執行的 Windows Form 應用程式的能力。 您可以使用 Visual Studio 建立使用 Windows Form 應用程式和使用者介面。 Windows Form 應用程式為基礎的類別<xref:System.Windows.Forms>命名空間。</xref:System.Windows.Forms>  
  
## <a name="designing-windows-forms-applications"></a>設計 Windows Form 應用程式  
 您可以建立 Windows Form 和 Windows 服務應用程式與[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱下列主題：  
  
-   [開始使用 Windows Form](https://msdn.microsoft.com/library/ms229601.aspx)。 提供如何建立和撰寫 Windows Form 上的資訊。  
   
-   [Windows Form 控制項](https://msdn.microsoft.com/library/ettb6e2a.aspx)。 主題詳細說明使用 Windows Form 控制項的集合。  
  
-   [Windows 服務應用程式](https://msdn.microsoft.com/library/y817hyb6.aspx)。 列出主題，說明如何建立 Windows 服務。  
  
## <a name="building-rich-interactive-user-interfaces"></a>建置豐富、互動式的使用者介面  
 Windows Form 是智慧型用戶端元件[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]，一組受管理的程式庫可讓一般的應用程式工作，例如讀取和寫入檔案系統。 使用類似的開發環境[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]，您可以透過網路與遠端電腦建立 Windows Form 應用程式顯示資訊、 要求輸入使用者，以及進行通訊。  
  
 在 Windows Form 表單是視覺化介面，在其顯示資訊給使用者。 通常，您會建置 Windows Form 應用程式將放在表單上的控制項，並開發對使用者動作，例如滑鼠點按或是按鍵的回應。 A*控制項*是獨立的使用者介面 (UI) 項目可顯示資料或接受資料輸入。  
  
### <a name="events"></a>事件  
 當使用者執行您的表單或其中一個控制項時，它會產生事件。 您的應用程式會使用程式碼對這些事件做出反應，並且在事件發生時加以處理。 如需詳細資訊，請參閱[Windows Form 中建立事件處理常式](https://msdn.microsoft.com/library/dacysss4.aspx)。  
  
### <a name="controls"></a>控制項  
 Windows Form 包含各種可以放在表單的控制項︰ 顯示文字方塊、 按鈕、 下拉式清單方塊、 選項按鈕和甚至網頁的控制項。 您可以在表單中使用的所有控制項的清單，請參閱[Windows Form 上使用的控制項](https://msdn.microsoft.com/library/3xdhey7w.aspx)。 如果現有的控制項不符合您的需求，Windows Form 也支援建立您自己的自訂控制項，使用<xref:System.Windows.Forms.UserControl>類別。</xref:System.Windows.Forms.UserControl>  
  
 Windows Form 有豐富的 UI 控制項，可以模擬高階應用程式 (例如 Microsoft Office) 中的功能。 使用<xref:System.Windows.Forms.ToolStrip>和<xref:System.Windows.Forms.MenuStrip>控制項，您可以建立包含文字和影像、 顯示子功能表，以及裝載其他控制項，例如文字方塊和下拉式方塊的工具列和功能表。</xref:System.Windows.Forms.MenuStrip> </xref:System.Windows.Forms.ToolStrip>  
  
 使用[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]拖放表單設計工具中，您可以輕鬆建立 Windows Form 應用程式︰ 只選取您的游標控制項，然後將它們放置您想要用在表單上。 設計工具提供像是格線和 「 對齊線 」 的工具可讓您輕鬆對齊控制項。 不論您是使用[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]編譯或在命令列中，您可以使用<xref:System.Windows.Forms.FlowLayoutPanel>，<xref:System.Windows.Forms.TableLayoutPanel>和<xref:System.Windows.Forms.SplitContainer>控制項來建立進階表單配置最短的時間和精力。</xref:System.Windows.Forms.SplitContainer> </xref:System.Windows.Forms.TableLayoutPanel> </xref:System.Windows.Forms.FlowLayoutPanel>  
  
### <a name="custom-ui-elements"></a>自訂 UI 項目  
 最後，您必須建立您自己自訂的 UI 項目，如果<xref:System.Drawing>命名空間包含所有您需要呈現線條、 圓形和其他圖形，直接在表單上的類別。</xref:System.Drawing>  
  
 逐步解說使用這些功能的詳細資訊，請參閱下列說明主題。  
  
|以|請參閱|  
|--------|---------|  
|建立新的 Windows Form 應用程式使用[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]|[逐步解說︰ 建立簡單的 Windows Form](http://msdn.microsoft.com/en-us/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|在表單上使用控制項|[如何︰ 將控制項加入 Windows Form](https://msdn.microsoft.com/library/0h5y8567.aspx)|   
|建立與圖形<xref:System.Drawing></xref:System.Drawing>|[圖形程式設計入門](https://msdn.microsoft.com/library/da0f23z7.aspx)|  
|建立自訂控制項|[如何︰ 繼承自 UserControl 類別](https://msdn.microsoft.com/library/00ctb4z0.aspx)|  
  
## <a name="displaying-and-manipulating-data"></a>顯示和操作資料  
 許多應用程式必須顯示來自資料庫、XML 檔案、XML Web 服務或其他資料來源的資料。 Windows Form 提供名為的彈性控制項<xref:System.Windows.Forms.DataGridView>控制項呈現傳統資料列和資料行格式，這類表格式資料，使每一項資料佔有自己的儲存格。</xref:System.Windows.Forms.DataGridView> 使用<xref:System.Windows.Forms.DataGridView>您可以自訂個別儲存格的外觀、 鎖定任意資料列和資料行的位置，以及顯示儲存格中，還有其他功能的複雜控制項。</xref:System.Windows.Forms.DataGridView>  
  
 利用 Windows Form 智慧型用戶端，透過網路連接到資料來源是一項簡單的工作。 <xref:System.Windows.Forms.BindingSource>元件中的 Windows Form 的新[!INCLUDE[vsprvslong](../../../csharp/misc/includes/vsprvslong_md.md)]和[!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)]連接到資料來源，並公開將資料繫結至控制項，瀏覽至上一頁和下一頁記錄、 編輯記錄，以及將變更儲存回原始來源的方法。</xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator>控制項提供一個簡單的介面，透過<xref:System.Windows.Forms.BindingSource>元件的使用者記錄之間巡覽。</xref:System.Windows.Forms.BindingSource> </xref:System.Windows.Forms.BindingNavigator>  
  
### <a name="data-bound-controls"></a>資料繫結控制項  
 您可以建立資料繫結控制項輕鬆地使用資料來源視窗中，顯示您專案中的資料來源，例如資料庫、 Web 服務和物件。 將項目從這個視窗拖曳到專案中的表單上，即可建立資料繫結控制項。 您也可以將物件從 [資料來源] 視窗拖曳至現有的控制項，以將現有的控制項繫結至資料。  
  
### <a name="settings"></a>設定  
 您可以管理在 Windows Form 資料繫結的另一種是設定。 大部分的智慧型用戶端應用程式必須保留其執行階段狀態，例如表單最後已知大小相關的一些資訊，並保留使用者喜好設定資料，例如儲存檔案的預設位置。 應用程式設定功能可滿足這些需求所提供的簡單方法來儲存兩種設定用戶端電腦上。 一旦定義之後使用[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]或程式碼編輯器 中，這些設定會保存為 XML，並且在執行階段自動讀回記憶體。  
  
 逐步解說使用這些功能的詳細資訊，請參閱下列說明主題。  
  
|以|請參閱|  
|--------|---------|  
|使用<xref:System.Windows.Forms.BindingSource>元件</xref:System.Windows.Forms.BindingSource>|[如何︰ 繫結 Windows Form 控制項和 BindingSource 元件使用設計工具](https://msdn.microsoft.com/library/801dxw2t.aspx)|  
|使用[!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]資料來源|[如何︰ 排序和篩選 ADO.NET 資料使用 Windows Form BindingSource 元件](https://msdn.microsoft.com/library/ya3sah92.aspx)|  
|使用 資料來源視窗|[逐步解說：顯示 Windows Form 上的資料](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>將應用程式部署到用戶端電腦  
 一旦您撰寫應用程式，您必須傳送到您的使用者，使他們可以安裝及執行自己的用戶端電腦上。 使用[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]技術，您可以部署應用程式內[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]藉由按幾下滑鼠，和使用者提供指向您在網站上的應用程式的 URL。 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]管理的所有項目和您的應用程式中的相依性，並確保應用程式已正確安裝用戶端電腦上。  
  
 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] 應用程式可以設定為只在使用者連線到網路時執行，或是線上和離線時都可執行。 當您指定應用程式應該支援離線作業時，[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]將連結加入至您的應用程式在使用者的**啟動** 功能表上，以便使用者可以開啟它而不使用的 URL。  
  
 當您更新應用程式時，您可以將新的部署資訊清單和新的應用程式複本發行到 Web 伺服器。 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]偵測到有可用的更新並升級使用者的安裝。沒有自訂的程式設計，才能更新舊組件。  
  
 如需完整介紹[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]，請參閱[ClickOnce 安全性和部署](https://docs.microsoft.com/visualstudio/deployment/clickonce-security-and-deployment)。 如需使用這些功能的逐步資訊，請參閱下列說明主題︰  
  
|以|請參閱|  
|--------|---------|  
|部署應用程式[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]|[如何：使用發行精靈發行 ClickOnce 應用程式](https://docs.microsoft.com/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [逐步解說：手動部署 ClickOnce 應用程式](https://docs.microsoft.com/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|更新[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]部署|[如何：管理 ClickOnce 應用程式的更新](https://docs.microsoft.com/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|管理與安全性[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]|[如何：啟用 ClickOnce 安全性設定](https://docs.microsoft.com/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>其他控制項和功能  
 Windows Form 中還有許多其他功能，可讓您快速、輕鬆地實作一般工作，例如支援建立對話方塊、列印、加入說明和文件，以及將您的應用程式當地語系化為多種語言。 此外，Windows Form 仰賴強固的安全性系統的[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]，讓您可以發行更安全的應用程式給您的客戶。  
  
 如需使用這些功能的逐步資訊，請參閱下列說明主題︰  
  
|以|請參閱|  
|--------|---------|  
|列印表單的內容|[如何︰ 列印 Windows Form 中的圖形](https://msdn.microsoft.com/library/741a0ktc.aspx)<br /><br /> [如何︰ 列印 Windows Form 中的多頁文字檔](https://msdn.microsoft.com/library/cwbe712d.aspx)|   
|深入了解 Windows Form 安全性|[安全性的 Windows Form 概觀](https://msdn.microsoft.com/library/90k49ccb.aspx)|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Windows Form 概觀](https://msdn.microsoft.com/library/8bxxy49h.aspx)   
 [My.Forms 物件](../../../visual-basic/language-reference/objects/my-forms-object.md)
