---
title: "WPF 中的文件 | Microsoft Docs"
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
  - "瀏覽器可檢視的文件"
  - "文件, 瀏覽器可檢視"
  - "文件, 控制項"
  - "文件, 封裝"
  - "文件, 文字配置"
  - "文件, 類型"
  - "文件, XPS"
  - "封裝文件"
  - "XPS 文件"
ms.assetid: 6e8db7bc-050a-4070-aa72-bb8c46e87ff8
caps.latest.revision: 36
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 35
---
# WPF 中的文件
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 所提供的各種文件功能可以建立高精確度的內容，此種內容的設計會比在舊版 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 中更加容易存取與閱讀。  除了增強的功能與品質以外，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 還提供文件顯示、封裝 \(Package\) 和安全性的整合式服務。  本主題提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文件類型與文件封裝的簡介。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="types_of_documents"></a>   
## 文件的類型  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 根據文件的預期用途將文件分為兩大類，這兩種文件分類稱為「固定格式文件」與「非固定格式文件」。  
  
 固定格式文件適合需要精確[!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] 展示的應用程式，與所用的顯示器或印表機硬體無關。  固定格式文件一般用於桌上出版、文書處理、表單配置等，這些都必須嚴格遵循原始的頁面設計。  固定格式文件會在其配置中維護內容項目的精確位置，不受使用中的顯示器或列印裝置影響。  例如，在 96 dpi 顯示器上檢視的固定格式文件頁面，不論是輸出到 600 dpi 雷射印表機或輸出到 4800 dpi 相紙輸出機，看起來都完全一樣。  文件品質會充分發揮各裝置的性能，但頁面配置永遠相同。  
  
 相較之下，非固定格式文件的設計用意是為了將檢視及可讀性最佳化，當讀取方便是主要的文件使用考量時，非固定格式文件便能達到最佳使用狀況。  非固定格式文件並不會設為某種預先定義的配置，而是會根據執行階段變數 \(如視窗大小、裝置解析度和選擇性的使用者偏好設定\)，動態調整及重新排列其內容。  網頁是一種簡單的非固定格式文件範例，其中的頁面內容會動態進行格式化，以配合目前的視窗。  非固定格式文件會根據執行階段環境，讓使用者擁有最佳的檢視和讀取經驗。  例如，同一份非固定格式文件在高解析度 19 吋顯示器或小型 2x3 吋 PDA 螢幕上都會動態重新格式化，以獲得最佳可讀性。  此外，非固定格式文件具備許多內建功能，包括搜尋、將可讀性最佳化的檢視模式，以及變更字型大小與外觀的能力。  請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)，以取得非固定格式文件的說明、範例和深入資訊。  
  
<a name="document_viewer"></a>   
## 文件控制項和文字配置  
 [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] 會提供一組預先建置的控制項，可簡化在應用程式中使用固定格式文件、非固定格式文件和一般文字的狀況。  使用 <xref:System.Windows.Controls.DocumentViewer> 控制項可以支援固定格式文件內容的顯示。  非固定格式文件內容的顯示則由三個不同的控制項支援：<xref:System.Windows.Controls.FlowDocumentReader>、<xref:System.Windows.Controls.FlowDocumentPageViewer> 和 <xref:System.Windows.Controls.FlowDocumentScrollViewer>，這三個控制項分別對應至不同使用者案例，請參閱下列各節。  其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項提供簡化的配置，以支援一般文字用途 \(請參閱下方的[使用者介面中的文字](#text_in_the_user_interface)\)。  
  
### 固定格式文件控制項 \- DocumentViewer  
 <xref:System.Windows.Controls.DocumentViewer> 控制項是設計用來顯示 <xref:System.Windows.Documents.FixedDocument> 內容。  <xref:System.Windows.Controls.DocumentViewer> 控制項提供的直覺式使用者介面可提供一般作業的內建支援，其中包含列印輸出、複製到剪貼簿、縮放及文字搜尋功能。  此控制項可透過常見的捲動機制，提供內容頁面的存取。  就像所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項一樣，<xref:System.Windows.Controls.DocumentViewer> 可支援完整或部分樣式重新設定，而讓此控制可以視覺化方式整合至任何應用程式或環境中。  
  
 <xref:System.Windows.Controls.DocumentViewer> 的設計是以唯讀方式顯示內容，不支援內容的編輯或修改。  
  
<a name="flow_document"></a>   
### 非固定格式文件控制項  
 **注意：**如需非固定格式文件功能及其建立方式的詳細資訊，請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)。  
  
 下列三個控制項可支援非固定格式文件內容的顯示：<xref:System.Windows.Controls.FlowDocumentReader>、<xref:System.Windows.Controls.FlowDocumentPageViewer> 和 <xref:System.Windows.Controls.FlowDocumentScrollViewer>。  
  
#### FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> 包含可讓使用者動態選擇各種檢視模式的功能，包括單頁 \(一次顯示一頁\) 檢視模式、雙頁 \(書本閱讀格式\) 檢視模式，以及連續捲動 \(無底邊\) 檢視模式。  如需這些檢視模式的詳細資訊，請參閱 <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>。  如果您不需要動態切換不同檢視模式的功能，則 <xref:System.Windows.Controls.FlowDocumentPageViewer> 和 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 可提供較輕量的非固定格式內容檢視器，這兩種會固定使用特定的檢視模式。  
  
#### FlowDocumentPageViewer 和 FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> 會以一次顯示一頁的檢視模式顯示內容，而 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 會以連續捲動模式顯示內容。  <xref:System.Windows.Controls.FlowDocumentPageViewer> 和 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 都有固定的特定檢視模式。  相較之下，<xref:System.Windows.Controls.FlowDocumentReader> 包含的功能可讓使用者動態選擇各種檢視模式 \(如 <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> 列舉型別所提供\)，但代價是比 <xref:System.Windows.Controls.FlowDocumentPageViewer> 或 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 需要更多資源。  
  
 預設一定會顯示垂直捲軸，而水平捲動會視需要顯示。  <xref:System.Windows.Controls.FlowDocumentScrollViewer> 的預設 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 不包含工具列，不過 <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> 屬性可用來啟用內建工具列。  
  
<a name="text_in_the_user_interface"></a>   
### 使用者介面中的文字  
 除了將文字加入至文件之外，文字顯然也可以在應用程式 UI \(例如表單\) 中使用。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含多個將文字繪製至螢幕的控制項。  每個控制項都鎖定不同的案例，而且擁有自己的功能與限制清單。  一般而言，在需要有限的文字支援 \(例如[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中的簡短句子\) 時，應該使用 <xref:System.Windows.Controls.TextBlock> 項目。  而在需要最少文字支援時，則可使用 <xref:System.Windows.Controls.Label>。  如需詳細資訊，請參閱 [TextBlock 概觀](../../../../docs/framework/wpf/controls/textblock-overview.md)。  
  
<a name="packaging"></a>   
## 文件封裝  
 <xref:System.IO.Packaging> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 提供的有效方法，可以組織應用程式資料、文件內容，以及容易存取、可攜式且容易散發之單一容器中的相關資源。  ZIP 檔就是能夠將多個物件當做一個單位保留之 <xref:System.IO.Packaging.Package> 類型的範例。  封裝 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 會提供使用「開放式封裝慣例」標準與 XML 和 ZIP 檔案架構所設計的預設 <xref:System.IO.Packaging.ZipPackage> 實作。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封裝 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 可以輕易建立封裝，以及儲存和存取其中的物件。  儲存在 <xref:System.IO.Packaging.Package> 中的物件就是指 <xref:System.IO.Packaging.PackagePart> \(「組件」\)。  封裝也可以包含簽署的數位憑證，該憑證可用於識別組件的發行者及驗證封裝內容是否未經修改。  封裝也可以包含 <xref:System.IO.Packaging.PackageRelationship> 功能，此功能允許將其他資訊加入至封裝或與特定組件產生關聯，而不需實際修改現有組件的內容。  封裝服務也支援 [!INCLUDE[TLA#tla_rm](../../../../includes/tlasharptla-rm-md.md)]。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封裝架構可以做為許多重要技術的基礎：  
  
-   符合 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] 的 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 文件。  
  
-   Microsoft Office "12" Open XML 格式文件 \(.docx\)。  
  
-   適用於您自己應用程式設計的自訂儲存格式。  
  
 以封裝 API 為基礎，為了儲存 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 固定格式內容文件而特別設計了 <xref:System.Windows.Xps.Packaging.XpsDocument>。  <xref:System.Windows.Xps.Packaging.XpsDocument> 為獨立的 \(Self\-Contained\) 文件，可以在檢視器中開啟、在 <xref:System.Windows.Controls.DocumentViewer> 控制項中顯示、傳送至列印多工緩衝區，或直接輸出至 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 相容的印表機。  
  
 下列章節提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附之 <xref:System.IO.Packaging.Package> 和 <xref:System.Windows.Xps.Packaging.XpsDocument> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 的其他資訊。  
  
<a name="packages"></a>   
### 封裝元件  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封裝 API 可以將應用程式資料和文件組織成單一可攜式單位。  ZIP 檔案就是其中一種最常見的封裝類型，而且是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所隨附的預設封裝類型。  <xref:System.IO.Packaging.Package> 本身是一個抽象類別，從此類別中可以使用開放標準 XML 和 ZIP 檔案架構實作 <xref:System.IO.Packaging.ZipPackage>。  <xref:System.IO.Packaging.Package.Open%2A> 方法會使用 <xref:System.IO.Packaging.ZipPackage>，依預設建立及使用 ZIP 檔案。  封裝可以包含三種基本項目類型：  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|應用程式內容、資料、文件和資源檔。|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|用於識別、驗證 \(Authentication\) 和驗證 \(Validation\) 的 [X.509 憑證](GTMT)。|  
|<xref:System.IO.Packaging.PackageRelationship>|與封裝或特定組件相關的新增資訊。|  
  
<a name="PackageParts"></a>   
#### PackageParts  
 <xref:System.IO.Packaging.PackagePart> \(「組件」\) 是一個抽象類別，就是指儲存在 <xref:System.IO.Packaging.Package> 中的物件。  在 ZIP 檔中，封裝組件會對應至 ZIP 檔內儲存的個別檔案。  <xref:System.IO.Packaging.ZipPackagePart> 可為 <xref:System.IO.Packaging.ZipPackage> 中儲存的可序列化物件提供預設實作。  就像檔案系統一樣，封裝內含的組件會儲存在階層式目錄或「資料夾形式」的組織中。  透過 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封裝 API，應用程式可以使用單一 ZIP 檔案容器，寫入、儲存及讀取多個 <xref:System.IO.Packaging.PackagePart> 物件。  
  
<a name="PackageDigitalSignatures"></a>   
#### PackageDigitalSignatures  
 基於安全理由，<xref:System.IO.Packaging.PackageDigitalSignature> \(「數位簽章」\) 可以與封裝內的組件產生關聯。  <xref:System.IO.Packaging.PackageDigitalSignature> 納入了 [509](GTMT)，可以提供兩項功能：  
  
1.  識別並驗證組件的建立者。  
  
2.  驗證組件未受到修改。  
  
 數位簽章不會防止組件遭到修改，但如果組件有任何改變，對於數位簽章的驗證檢查就會失敗。  然後，應用程式可以採取適當的動作，例如：防止開啟組件，或通知使用者該組件已遭修改，因此並不安全。  
  
<a name="PackageRelationships"></a>   
#### PackageRelationships  
 <xref:System.IO.Packaging.PackageRelationship> \(「關聯性」\) 提供的機制可以使其他資訊與封裝或封裝內的組件產生關聯。  關聯性為封裝層級機能，可以使其他資訊與組件產生關聯，而不需修改實際組件內容。  將新資料直接插入組件內容中，在許多情況下常不切實際：  
  
-   不知道組件與其內容結構描述的實際類型。  
  
-   即使知道，內容結構描述也不會提供用以加入新資訊的方法。  
  
-   組件可能會進行數位簽署或加密，以免遭到修改。  
  
 封裝關聯性會提供顯而易見的方法，用以新增或使其他資訊與個別組件或整個封裝產生關聯。  封裝關聯性可用於兩項主要功能：  
  
1.  定義某個組件與另一個組件的相依性關係。  
  
2.  定義資訊關聯性，以便新增組件的相關注意事項或其他資料。  
  
 <xref:System.IO.Packaging.PackageRelationship> 會提供迅速而明顯的方法，用以定義相依性及新增與封裝組件或整個封裝相關聯的其他資訊。  
  
<a name="Dependency_Relationships"></a>   
##### 相依性關係  
 相依性關係用於描述某個組件與其他組件的相依性。  例如，封裝所含的 HTML 組件包含了一個或多個 \<img\> 影像標記。  影像標記所參考的影像就是位於封裝內部或外部的其他組件 \(例如可以透過網際網路存取\)。  建立與 HTML 檔相關聯的 <xref:System.IO.Packaging.PackageRelationship>，即可輕易快速地探索和存取相依資源。  不必知道結構描述或剖析文件，瀏覽器或檢視器應用程式便可直接存取組件關聯性，並立即開始組合相依資源。  
  
<a name="Information_Relationships"></a>   
##### 資訊關聯性  
 <xref:System.IO.Packaging.PackageRelationship> 類似於注意事項或附註，也可以用於儲存要與組件相關聯之其他類型的資訊，而不需實際修改組件內容本身。  
  
<a name="XPS_Documents"></a>   
## XPS 文件  
 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] 文件是一種封裝，內含一份或多份固定格式文件和進行呈現所需的所有資源與資訊。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 也是原生的 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] 列印多工緩衝檔案格式。  <xref:System.Windows.Xps.Packaging.XpsDocument> 會儲存在標準 ZIP 資料集中，而且可以包含 XML 和二進位元件的組合 \(例如影像和字型檔案\)。[PackageRelationships](#PackageRelationships) 用於定義要完全呈現文件所需的內容和資源之間的相依性。  <xref:System.Windows.Xps.Packaging.XpsDocument> 設計提供的單一、高精確度文件解決方案，可以支援下列多種用途：  
  
-   將固定格式文件的內容與資源當做單一可攜式且容易散發的檔案，進行讀取、寫入及儲存。  
  
-   使用 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 檢視器應用程式顯示文件。  
  
-   以 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] 的原生列印多工緩衝輸出格式來輸出文件。  
  
-   將文件直接傳送到與 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 相容的印表機。  
  
## 請參閱  
 <xref:System.Windows.Documents.FixedDocument>   
 <xref:System.Windows.Documents.FlowDocument>   
 <xref:System.Windows.Xps.Packaging.XpsDocument>   
 <xref:System.IO.Packaging.ZipPackage>   
 <xref:System.IO.Packaging.ZipPackagePart>   
 <xref:System.IO.Packaging.PackageRelationship>   
 <xref:System.Windows.Controls.DocumentViewer>   
 [文字](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)   
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [文件序列化與儲存](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)