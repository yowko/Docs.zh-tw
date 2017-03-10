---
title: "Windows Forms Application Basics (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Windows applications"
  - "Windows Forms, Visual Basic"
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Windows Forms Application Basics (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中非常重要的一個部分是能夠建立在使用者本機電腦上執行的 Windows Form 應用程式。  您可以使用Visual Studio來建立應用程式和使用者介面使用Windows Forms。   Windows Form 應用程式是以 <xref:System.Windows.Forms> 命名空間的類別 \(Class\) 為基礎建置而成。  
  
## 設計 Windows Form 應用程式  
 您可以使用 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 建立 Windows Form 和 Windows 服務應用程式。  如需詳細資訊，請參閱下列主題：  
  
-   [Windows Form 使用者入門](../Topic/Getting%20Started%20with%20Windows%20Forms.md).  提供如何建立和撰寫 Windows Form 程式的資訊。  
  
-   [Windows Forms Walkthroughs](http://msdn.microsoft.com/zh-tw/fd44d13d-4733-416f-aefc-32592e59e5d9).  列出提供以 Windows Form 為基礎逐步開發一般所建立之 Windows Form 應用程式的主題。  
  
-   [Windows Form 控制項](../Topic/Windows%20Forms%20Controls.md).  詳述 Windows Form 控制項用法的主題集合。  
  
-   [Windows 服務應用程式](../Topic/Developing%20Windows%20Service%20Applications.md).  列出說明如何建立 Windows 服務的主題。  
  
## 建置豐富的互動式使用者介面  
 Windows Form 是 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 的一種智慧型用戶端元件，它是一組 Managed 程式庫，可以用於執行一般應用程式工作，例如讀取和寫入檔案系統。  使用 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 這類的開發環境，您就可以建立能夠顯示資訊、要求使用者輸入，以及透過網路與遠端電腦通訊的 Windows Form 應用程式。  
  
 在 Windows Form 中，表單是您向使用者顯示資訊的視覺化介面。  通常建置 Windows Form 應用程式的方法為在表單上放置控制項，然後開發對使用者動作 \(例如按下滑鼠或按鍵\) 的回應。  「*控制項*」\(Control\) 是一種獨立的使用者介面 \(UI\) 元素，可以顯示資料或接受輸入的資料。  
  
### 事件  
 當使用者對表單或其中一個控制項執行動作時，會產生事件。  應用程式會使用程式碼回應這些事件，並在發生事件時加以處理。  如需詳細資訊，請參閱 [在 Windows Form 中建立事件處理常式](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)。  
  
### 控制項  
 Windows Form 包含各種您可以置於表單上的控制項，像是顯示文字方塊、按鈕、下拉式方塊、選項按鈕，甚至網頁的控制項。  如需可以在表單上使用之所有控制項的清單，請參閱[在 Windows Form 上使用的控制項](../Topic/Controls%20to%20Use%20on%20Windows%20Forms.md)。  如果現有控制項不符合您的需要，Windows Form 也支援您使用 <xref:System.Windows.Forms.UserControl> 類別建立自訂控制項。  
  
 Windows Form 具有豐富的 UI 控制項，可以模擬像 Microsoft Office 這樣的高階應用程式的功能。  使用 <xref:System.Windows.Forms.ToolStrip> 和 <xref:System.Windows.Forms.MenuStrip> 控制項，您可以建立包含文字與影像、顯示子功能表，以及裝載 \(Host\) 其他控制項 \(如文字方塊和下拉式方塊\) 的工具列與功能表。  
  
 透過 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 的拖放表單設計工具，您可以輕鬆地建立 Windows Form 應用程式，只要以游標選取控制項，再將控制項置於表單上想要放置的地方即可。  設計工具提供像是格線和「對齊線」這類的工具，可以解決對齊控制項的煩惱。  不論是使用 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 或在命令列進行編譯，您都可以使用 <xref:System.Windows.Forms.FlowLayoutPanel>、<xref:System.Windows.Forms.TableLayoutPanel> 和 <xref:System.Windows.Forms.SplitContainer> 控制項，以最少的時間和心力建立進階表單配置。  
  
### 自訂 UI 項目  
 最後，如果您必須建立自訂 UI 項目，則 <xref:System.Drawing> 命名空間包含了直接在表單上呈現線條、圓形和其他圖案所需的所有類別。  
  
 如需使用這些功能的逐步資訊，請參閱下列說明主題。  
  
|若要|請參閱|  
|--------|---------|  
|使用 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 建立新的 Windows Form 應用程式|[Walkthrough: Creating a Simple Windows Form](http://msdn.microsoft.com/zh-tw/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|在表單上使用控制項|[如何：將控制項加入至 Windows Form](../Topic/How%20to:%20Add%20Controls%20to%20Windows%20Forms.md)|  
|從表單和控制項處理事件|[How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/zh-tw/8461e9b8-14e8-406f-936e-3726732b23d2)|  
|使用 <xref:System.Windows.Forms.ToolStrip> 控制項|[如何：使用設計工具建立具有標準項目的基本 ToolStrip](../Topic/How%20to:%20Create%20a%20Basic%20Windows%20Forms%20ToolStrip%20with%20Standard%20Items%20Using%20the%20Designer.md)|  
|以 <xref:System.Drawing> 建立圖形|[圖形程式設計入門](../Topic/Getting%20Started%20with%20Graphics%20Programming.md)|  
|建立自訂控制項|[如何：繼承自 UserControl 類別](../Topic/How%20to:%20Inherit%20from%20the%20UserControl%20Class.md)|  
  
## 顯示和管理資料  
 許多應用程式都必須顯示來自資料庫、XML 檔案、XML Web Service 或其他資料來源的資料。  Windows Form 提供一個富彈性的控制項 \(名為 <xref:System.Windows.Forms.DataGridView>\)，可以用傳統的資料行與資料列格式呈現這類的表格式資料，使每一項資料都有自己的儲存格空間。  使用 <xref:System.Windows.Forms.DataGridView>，您可以使用許多功能，像是自訂個別儲存格的外觀、將任意資料列和資料行鎖定、顯示儲存格內複雜的控制項等等。  
  
 連接網路上的資料來源在 Windows Form 智慧型用戶端中是一項很簡單的工作。  [!INCLUDE[vsprvslong](../../../csharp/misc/includes/vsprvslong-md.md)] 和 [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong-md.md)] 中新增的 Windows Form 元件 <xref:System.Windows.Forms.BindingSource> 表示與資料來源的連接，同時也公開方法將資料繫結至控制項、巡覽至上一筆和下一筆記錄、編輯記錄以及將變更存回原始來源。  <xref:System.Windows.Forms.BindingNavigator> 控制項則透過 <xref:System.Windows.Forms.BindingSource> 元件，提供使用者在記錄之間進行巡覽的介面。  
  
### 資料繫結控制項  
 您可以輕易地使用 \[資料來源\] 視窗建立資料繫結控制項，此視窗會顯示像專案中的資料庫、Web 服務以及物件等的資料來源。  您可以從此視窗將項目拖曳至專案中的表單，建立資料繫結控制項。  您也可以從 \[資料來源\] 視窗，將物件拖曳至現有的控制項，將現有的控制項連接到資料。  
  
### 設定  
 另一種您可以在 Windows Form 中管理的資料繫結 \(Data Binding\) 類型就是設定。  大部分的智慧型用戶端應用程式必須保留一些關於本身執行階段狀態的資訊 \(例如表單上次的大小\) 和使用者喜好設定資料 \(例如已儲存檔案的預設位置\)。  應用程式設定功能提供簡易的方式，在用戶端電腦上同時儲存兩種類型的設定，輕鬆地滿足了這些需求。  一旦使用 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 或程式碼編輯器定義設定後，這些設定就會保存為 XML，並自動在執行階段讀回記憶體。  
  
 如需使用這些功能的逐步資訊，請參閱下列說明主題。  
  
|若要|請參閱|  
|--------|---------|  
|使用 <xref:System.Windows.Forms.BindingSource> 元件|[如何：使用設計工具將 Windows Form 控制項和 BindingSource 元件加以繫結](../Topic/How%20to:%20Bind%20Windows%20Forms%20Controls%20with%20the%20BindingSource%20Component%20Using%20the%20Designer.md)|  
|處理 [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] 資料來源|[如何：使用 Windows Form BindingSource 元件排序和篩選 ADO.NET 資料](../Topic/How%20to:%20Sort%20and%20Filter%20ADO.NET%20Data%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)|  
|使用 \[資料來源\] 視窗|[逐步解說：顯示 Windows Form 上的資料](../Topic/Walkthrough:%20Displaying%20Data%20on%20a%20Windows%20Form.md)|  
|使用應用程式設定|[How to: Create Application Settings Using the Designer](http://msdn.microsoft.com/zh-tw/53b3af80-1c02-4e35-99c6-787663148945)|  
  
## 將應用程式部署到用戶端電腦  
 撰寫完應用程式之後，您就必須將它傳送給使用者，供使用者自行在用戶端電腦上安裝和執行。  使用 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 技術，只需按幾下滑鼠按鍵就可以從 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 中部署應用程式，並為使用者提供指向 Web 上應用程式的 URL。  [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 會管理應用程式中所有的項目和相依性，並確保應用程式能夠正確地安裝在用戶端電腦上。  
  
 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 應用程式可以設定成只在使用者連線到網路時才執行，或者是設定成連線和離線時都可以執行。  當您指定某個應用程式必須支援離線作業時，[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 會在使用者的 \[**開始**\] 功能表中加入應用程式的連結，讓使用者不必使用 URL 即可開啟應用程式。  
  
 當您更新應用程式時，要將新的部署資訊清單以及新的應用程式複本發行至 Web 伺服器。  [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 會偵測到可用的更新，並升級使用者的安裝。更新舊的組件並不需要自訂程式設計。  
  
 如需 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 的完整介紹，請參閱 [ClickOnce 安全性和部署](/visual-studio/deployment/clickonce-security-and-deployment)。  如需使用這些功能的逐步資訊，請參閱下列說明主題：  
  
|若要|請參閱|  
|--------|---------|  
|使用 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 部署應用程式|[如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)<br /><br /> [逐步解說：手動部署 ClickOnce 應用程式](../Topic/Walkthrough:%20Manually%20Deploying%20a%20ClickOnce%20Application.md)|  
|更新 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 部署|[如何：管理 ClickOnce 應用程式中的更新](../Topic/How%20to:%20Manage%20Updates%20for%20a%20ClickOnce%20Application.md)|  
|使用 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 管理安全性|[如何：啟用 ClickOnce 安全性設定](../Topic/How%20to:%20Enable%20ClickOnce%20Security%20Settings.md)|  
  
## 其他控制項和功能  
 Windows Form 中還有許多其他功能可以讓您輕鬆快速地實作一般工作，例如支援建立對話方塊、列印、加入說明和文件，以及將應用程式翻譯成多種語言。  此外，Windows Form 採用 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 強固的安全性系統，讓您將更安全的應用程式發行給客戶。  
  
 如需使用這些功能的逐步資訊，請參閱下列說明主題：  
  
|若要|請參閱|  
|--------|---------|  
|列印表單的內容|[如何：列印 Windows Form 中的圖形](../Topic/How%20to:%20Print%20Graphics%20in%20Windows%20Forms.md)<br /><br /> [如何：在 Windows Form 中列印多頁文字檔](../Topic/How%20to:%20Print%20a%20Multi-Page%20Text%20File%20in%20Windows%20Forms.md)|  
|將 Windows Form 應用程式翻譯成各國語言|[Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)|  
|進一步了解 Windows Form 安全性|[Windows Form 中的安全性概觀](../Topic/Security%20in%20Windows%20Forms%20Overview.md)|  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Windows Form 概觀](../Topic/Windows%20Forms%20Overview.md)   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)