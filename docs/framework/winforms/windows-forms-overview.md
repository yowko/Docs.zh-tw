---
title: "Windows Form 概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "智慧型用戶端"
  - "Windows Form, 關於 Windows Form"
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 34
---
# Windows Form 概觀
以下概觀將討論智慧型用戶端應用程式的優點、Windows Form 程式設計的主要功能，以及如何使用 Windows Form 來建置智慧型用戶端，以符合當今企業和使用者的需求。  
  
## Windows Form 和智慧型用戶端應用程式  
 使用 Windows Form 來開發智慧型用戶端。  *「智慧型用戶端」*\(smart client\) 是豐富的圖形化應用程式，容易部署及更新，無論是否連接至網際網路都能運作，而且在存取本機電腦上的資源時，所使用的方法比傳統的 Windows 應用程式更安全。  
  
### 建置豐富、互動式的使用者介面  
 Windows Form 是一種適用於 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 的智慧型用戶端技術，它是一組 Managed 程式庫，可簡化常見的應用程式工作，例如讀取和寫入檔案系統。  當您使用類似 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 的開發環境時，可以建立 Windows Form 智慧型用戶端應用程式來顯示資訊、要求使用者輸入，以及透過網路與遠端電腦通訊。  
  
 在 Windows Form 中，*「表單」*\(form\) 是一種視覺化介面，您可以在上面顯示要提供給使用者的資訊。  通常在建置 Windows Form 應用程式時，您會將控制項加入表單，以及開發對使用者動作的回應，例如滑鼠點選或是按下按鍵。  *「控制項」*\(control\) 是獨立的使用者介面 \(UI\) 項目，可顯示資料或接受資料輸入。  
  
 當使用者對您的表單或其中一個控制項執行某個動作時，該動作會產生事件。  您的應用程式會使用程式碼對這些事件做出反應，並且在事件發生時加以處理。  如需詳細資訊，請參閱[在 Windows Form 中建立事件處理常式](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)。  
  
 Windows Form 包含可讓您加入表單中的各種控制項：顯示文字方塊、按鈕、下拉式清單方塊、選項按鈕甚至網頁的控制項。  如需您可以在表單上使用之所有控制項的清單，請參閱[在 Windows Form 上使用的控制項](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)。  如果現有的控制項不符合您的需求，Windows Form 也支援使用 <xref:System.Windows.Forms.UserControl> 類別來建立您自己的自訂控制項。  
  
 Windows Form 有豐富的 UI 控制項，可以模擬高階應用程式 \(例如 Microsoft Office\) 中的功能。  當您使用 <xref:System.Windows.Forms.ToolStrip> 和 <xref:System.Windows.Forms.MenuStrip> 控制項時，您可以建立包含文字和影像的工具列和功能表、顯示子功能表，以及裝載其他控制項，例如文字方塊和下拉式方塊。  
  
 使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 拖放式 Windows Form 設計工具，可讓您輕鬆建立 Windows Form 應用程式。  只要用您的游標選取控制項，然後將其加入表單上您想要的位置即可。  設計工具提供像是格線和對齊線之類的工具，可讓您輕鬆對齊控制項。  不論您是使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或是在命令列中編譯，都可以使用 <xref:System.Windows.Forms.FlowLayoutPanel>、<xref:System.Windows.Forms.TableLayoutPanel> 和 <xref:System.Windows.Forms.SplitContainer> 控制項來建立進階表單配置，以節省時間。  
  
 最後，如果您必須建立自己的自訂 UI 項目，<xref:System.Drawing> 命名空間包含許多類別選項，可直接在表單上呈現線條、圓形和其他形狀。  
  
> [!NOTE]
>  Windows Form 控制項的設計並不能跨應用程式定義域來封送處理。  基於這個理由，Microsoft 不支援跨 <xref:System.AppDomain> 界限傳遞 Windows Form 控制項，即使 <xref:System.MarshalByRefObject> 的 <xref:System.Windows.Controls.Control> 基底類型似乎表示這是可行的。  只要沒有 Windows Form 控制項跨應用程式定義域界限傳遞，即可支援具有多個應用程式定義域的 Windows Form 應用程式。  
  
#### 建立表單和控制項的說明  
 如需如何使用這些功能的逐步解說資訊，請參閱下列說明主題。  
  
|描述|說明主題|  
|--------|----------|  
|在表單上使用控制項|[如何：將控制項加入至 Windows Form](../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|  
|使用 <xref:System.Windows.Forms.ToolStrip> 控制項|[如何：使用設計工具建立具有標準項目的基本 ToolStrip](../../../docs/framework/winforms/controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|  
|使用 <xref:System.Drawing> 建立圖形|[圖形程式設計入門](../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|建立自訂控制項|[如何：繼承自 UserControl 類別](../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
### 顯示和操作資料  
 許多應用程式必須顯示來自資料庫、XML 檔案、XML Web 服務或其他資料來源的資料。  Windows Form 提供名為 <xref:System.Windows.Forms.DataGridView> 控制項的彈性控制項，以傳統的資料列和資料行格式，來顯示這類表格式資料，讓每項資料佔有自己的儲存格。  當您使用 <xref:System.Windows.Forms.DataGridView> 時，您可以自訂個別儲存格的外觀、將任意資料列和資料行鎖定位置，以及顯示儲存格中的複雜控制項，還有其他功能。  
  
 利用 Windows Form 智慧型用戶端，透過網路連接到資料來源是一項簡單的工作。  <xref:System.Windows.Forms.BindingSource> 元件 \(Windows Form 在 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 和 [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] 中的新元件\) 提供連線至資料來源，並公開將資料繫結至控制項的方法：巡覽至上一筆和下一筆記錄、編輯記錄，以及將變更儲存回原始來源。  <xref:System.Windows.Forms.BindingNavigator> 控制項透過 <xref:System.Windows.Forms.BindingSource> 元件提供一個簡單的介面，可讓使用者在記錄之間巡覽。  
  
 您可以使用 \[資料來源\] 視窗，輕鬆地建立資料繫結控制項。  此視窗會顯示您專案中的資料來源，例如資料庫、Web 服務和物件。  將項目從這個視窗拖曳到專案中的表單上，即可建立資料繫結控制項。  您也可以將物件從 \[資料來源\] 視窗拖曳至現有的控制項，以將現有的控制項繫結至資料。  
  
 在 Windows Form 中，另一種管理資料繫結的方法是*「設定」*\(settings\)。  大部分的智慧型用戶端應用程式必須保留其執行階段狀態的一些相關資訊 \(例如表單的最後已知大小\)，以及保留使用者偏好設定資料 \(例如儲存檔案的預設位置\)。  應用程式設定功能為因應這些需求，提供了一種簡單的方法，可將這兩種設定都儲存在用戶端電腦上。  在使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或程式碼編輯器來定義這些設定之後，這些設定會保存為 XML，並且在執行階段自動讀回記憶體中。  
  
#### 顯示和操作資料的說明  
 如需如何使用這些功能的逐步解說資訊，請參閱下列說明主題。  
  
|描述|說明主題|  
|--------|----------|  
|使用 <xref:System.Windows.Forms.BindingSource> 元件|[如何：使用設計工具將 Windows Form 控制項和 BindingSource 元件加以繫結](../../../docs/framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|使用 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 資料來源|[如何：使用 Windows Form BindingSource 元件排序和篩選 ADO.NET 資料](../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|  
|使用資料來源視窗|[逐步解說：顯示 Windows Form 上的資料](../Topic/Walkthrough:%20Displaying%20Data%20on%20a%20Windows%20Form.md)|  
|使用應用程式設定|[如何：建立應用程式設定](../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)|  
  
### 將應用程式部署到用戶端電腦  
 撰寫應用程式之後，您必須將該應用程式傳送給您的使用者，讓它們能夠自己在用戶端電腦上安裝及執行該應用程式。  當您使用 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 技術時，只需要按幾下滑鼠，就可以從 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中部署應用程式，並可提供 URL 給使用者，指向您在網站上的應用程式。  [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 會管理您應用程式中的所有項目和相依性，並確保應用程式已正確安裝在用戶端電腦上。  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式可以設定為只在使用者連線到網路時執行，或是線上和離線時都可執行。  當您指定應用程式應該支援離線作業時，[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 會在使用者的 \[開始\] 功能表中加入應用程式的連結。  然後使用者就可以直接開啟應用程式，而不需要使用 URL。  
  
 當您更新應用程式時，您可以將新的部署資訊清單和新的應用程式複本發行到 Web 伺服器。  [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 會偵測到有可用的更新，並升級使用者的安裝 ，不需要自訂的程式設計，即可更新舊組件。  
  
#### 部署 ClickOnce 應用程式的說明  
 如需 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 的完整介紹，請參閱 [ClickOnce 安全性和部署](../Topic/ClickOnce%20Security%20and%20Deployment.md)。  如需如何使用這些功能的逐步解說資訊，請參閱下列說明主題。  
  
|描述|說明主題|  
|--------|----------|  
|使用 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 來部署應用程式|[如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)<br /><br /> [逐步解說：手動部署 ClickOnce 應用程式](../Topic/Walkthrough:%20Manually%20Deploying%20a%20ClickOnce%20Application.md)|  
|更新 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 部署|[如何：管理 ClickOnce 應用程式中的更新](../Topic/How%20to:%20Manage%20Updates%20for%20a%20ClickOnce%20Application.md)|  
|使用 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 來管理安全性|[如何：啟用 ClickOnce 安全性設定](../Topic/How%20to:%20Enable%20ClickOnce%20Security%20Settings.md)|  
  
### 其他控制項和功能  
 Windows Form 中還有許多其他功能，可讓您快速、輕鬆地實作一般工作，例如支援建立對話方塊、列印、加入說明和文件，以及將您的應用程式當地語系化為多種語言。  此外，Windows Form 仰賴 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 強固的安全性系統。  藉由這個系統，您可以發行更安全的應用程式給您的客戶。  
  
#### 實作其他控制項和功能的說明  
 如需如何使用這些功能的逐步解說資訊，請參閱下列說明主題。  
  
|描述|說明主題|  
|--------|----------|  
|列印表單的內容|[如何：列印 Windows Form 中的圖形](../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [如何：在 Windows Form 中列印多頁文字檔](../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|  
|深入了解 Windows Form 安全性|[Windows Form 中的安全性概觀](../../../docs/framework/winforms/security-in-windows-forms-overview.md)|  
  
## 請參閱  
 [Windows Form 使用者入門](../../../docs/framework/winforms/getting-started-with-windows-forms.md)   
 [建立新的 Windows Form](../../../docs/framework/winforms/creating-a-new-windows-form.md)   
 [ToolStrip 控制項概觀](../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [DataGridView 控制項概觀](../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)   
 [BindingSource 元件概觀](../../../docs/framework/winforms/controls/bindingsource-component-overview.md)   
 [應用程式設定概觀](../../../docs/framework/winforms/advanced/application-settings-overview.md)   
 [ClickOnce 安全性和部署](../Topic/ClickOnce%20Security%20and%20Deployment.md)