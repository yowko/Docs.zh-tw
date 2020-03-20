---
title: 文件
ms.date: 03/30/2017
helpviewer_keywords:
- documents [WPF], packaging
- documents [WPF], text layout
- documents [WPF], XPS
- 'XPS documents [WPF], , '
- documents [WPF], controls
- documents [WPF], types of
- documents [WPF], browser-viewable
ms.assetid: 6e8db7bc-050a-4070-aa72-bb8c46e87ff8
ms.openlocfilehash: e88604c42b253b48ee605f42f24fe301e339f74b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174676"
---
# <a name="documents-in-wpf"></a>WPF 中的文件
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供廣泛的文檔功能，能夠創建與前幾代 Windows 更易於訪問和讀取的高保真內容。 除了增強功能和品質，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也針對文件顯示、封裝和安全性提供整合式服務。 本主題提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文件類型和文件封裝的簡介。  

<a name="types_of_documents"></a>
## <a name="types-of-documents"></a>文件的類型  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 根據文件的預期用途將文件分為兩大類，這兩種文件分類稱為「固定格式文件」與「非固定格式文件」。  
  
 固定文檔適用于需要精確"您所看到的是您得到的內容"（WYSIWYG） 演示文稿的應用程式，而與所使用的顯示器或印表機硬體無關。 固定格式文件一般用於桌上出版、文書處理和表單配置，必須嚴格遵循原始頁面設計。 固定格式文件會在其配置中維持內容項目的精確位置，不受使用中的顯示器或列印裝置影響。 例如，在 96 dpi 顯示器上檢視的固定格式文件頁面，不論是輸出到 600 dpi 雷射印表機或輸出到 4800 dpi 相紙輸出機，看起來都完全一樣。 文件品質會充分發揮各裝置的性能，但頁面配置永遠相同。  
  
 相較之下，非固定格式文件的設計用意是為了將檢視及可讀性最佳化；如果容易閱讀是主要的文件使用考量，則最適合使用非固定格式文件。 非固定格式文件並不會設為某種預先定義的配置，而是會根據執行階段變數 (例如視窗大小、裝置解析度和選擇性的使用者喜好設定)，動態調整及自動重排其內容。 網頁即是一個簡單的非固定格式文件範例，其中的頁面內容會動態進行格式化，以符合目前視窗大小。 非固定格式文件會根據執行階段環境，讓使用者擁有最佳的檢視和閱讀體驗。 例如，同一份非固定格式文件在高解析度 19 吋顯示器或小型 2x3 吋 PDA 螢幕上都會動態重新格式化，以獲得最佳可讀性。 此外，非固定格式文件具備許多內建功能，包括搜尋、將可讀性最佳化的檢視模式，以及變更字型大小與外觀的能力。  如需非固定格式文件的說明、範例和深入資訊，請參閱[非固定格式文件概觀](flow-document-overview.md)。  
  
<a name="document_viewer"></a>
## <a name="document-controls-and-text-layout"></a>文件控制項和文字配置  
 .NET Framework 提供了一組預構建的控制項，可在應用程式中使用固定文檔、流文檔和常規文本進行簡化。  支援使用<xref:System.Windows.Controls.DocumentViewer>控制項顯示固定文檔內容。  流文檔內容的顯示由三個不同的控制項支援：<xref:System.Windows.Controls.FlowDocumentReader><xref:System.Windows.Controls.FlowDocumentPageViewer>和<xref:System.Windows.Controls.FlowDocumentScrollViewer>映射到不同使用者方案的哪些操作（請參閱下面的部分）。  其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項提供簡化的配置，以支援一般文字用途 (請參閱下方的[使用者介面中的文字](#text_in_the_user_interface))。  
  
### <a name="fixed-document-control---documentviewer"></a>固定格式文件控制項 - DocumentViewer  
 該<xref:System.Windows.Controls.DocumentViewer>控制項旨在顯示<xref:System.Windows.Documents.FixedDocument>內容。 該<xref:System.Windows.Controls.DocumentViewer>控制項提供了直觀的使用者介面，為常見操作提供內置支援，包括列印輸出、複製到剪貼簿、縮放和文本搜索功能。 此控制項可透過常見的捲動機制，來存取多頁內容。 與所有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項一樣<xref:System.Windows.Controls.DocumentViewer>，支援完全或部分重新設置，使控制項能夠直觀地集成到幾乎任何應用程式或環境中。  
  
 <xref:System.Windows.Controls.DocumentViewer>旨在以唯讀方式顯示內容;編輯或修改內容不可用，並且不受支援。  
  
<a name="flow_document"></a>
### <a name="flow-document-controls"></a>非固定格式文件控制項  

> [!NOTE]
> 有關流文檔功能以及如何創建它們的詳細資訊，請參閱[流文檔概述](flow-document-overview.md)。  
  
 流文檔內容的顯示由三個控制項支援： <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentPageViewer>和<xref:System.Windows.Controls.FlowDocumentScrollViewer>。  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>包括允許使用者在各種查看模式之間進行動態選擇的功能，包括單頁（一次頁面）查看模式、一次兩頁（圖書閱讀格式）查看模式和連續滾動（無底）查看模式。  有關這些查看模式的詳細資訊，請參閱<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>。  如果您不需要能夠在不同的查看模式之間動態切換，<xref:System.Windows.Controls.FlowDocumentPageViewer>並提供<xref:System.Windows.Controls.FlowDocumentScrollViewer>在特定查看模式下固定的較輕的流內容檢視器。  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer 和 FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>以一次頁面查看模式顯示內容，同時在<xref:System.Windows.Controls.FlowDocumentScrollViewer>連續滾動模式下顯示內容。  和<xref:System.Windows.Controls.FlowDocumentPageViewer><xref:System.Windows.Controls.FlowDocumentScrollViewer>都固定到特定的查看模式。 比較<xref:System.Windows.Controls.FlowDocumentReader>與 比較，其中包括允許使用者在各種查看模式（如枚<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>舉提供）之間進行動態選擇的功能，其代價是資源密集型大於<xref:System.Windows.Controls.FlowDocumentPageViewer>或<xref:System.Windows.Controls.FlowDocumentScrollViewer>。  
  
 預設一定會顯示垂直捲軸，而水平捲動則會視需要顯示。 的<xref:System.Windows.Controls.FlowDocumentScrollViewer>預設值[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]不包括工具列;如果但是，該<xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A>屬性可用於啟用內建工具列。  
  
<a name="text_in_the_user_interface"></a>
### <a name="text-in-the-user-interface"></a>使用者介面中的文字  
 除了將文字新增至文件，您顯然也能在表單等應用程式 UI 中使用文字。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含多個將文字繪製到螢幕的控制項。 每個控制項都是針對不同案例，而且有自己的功能與限制清單。 通常，當需要<xref:System.Windows.Controls.TextBlock>有限的文本支援時，應使用元素，例如 中的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]簡短句子。 <xref:System.Windows.Controls.Label>可在需要最少的文本支援時使用。 如需詳細資訊，請參閱 [TextBlock 概觀](../controls/textblock-overview.md)。  
  
<a name="packaging"></a>
## <a name="document-packaging"></a>文件封裝  
 API<xref:System.IO.Packaging>提供了一種高效的方法，用於將應用程式資料、文檔內容和相關資源組織到一個易於訪問、便於移植且易於分發的容器中。 ZIP 檔是一種類型的示例<xref:System.IO.Packaging.Package>，該類型能夠將多個物件作為單個單元保存。 打包 API 提供了使用帶有<xref:System.IO.Packaging.ZipPackage>XML 和 ZIP 檔體系結構的開放打包約定標準設計的預設實現。 打包[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]API 使創建包以及存儲和訪問其中的物件變得簡單。 存儲在 中<xref:System.IO.Packaging.Package>的物件稱為<xref:System.IO.Packaging.PackagePart>（"部分"）。 封裝也可以包含簽署的數位憑證，該憑證可用來識別組件的建立者，以及驗證封裝內容是否未遭修改。  包還包括一項<xref:System.IO.Packaging.PackageRelationship>功能，允許將附加資訊添加到包中或與特定部件關聯，而無需實際修改現有部件的內容。  包服務還支援微軟 Windows 版權管理 （RM）。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封裝架構是下列幾個重要技術的基礎：  
  
- XPS 文檔符合 XML 文件規格 （XPS）。  
  
- Microsoft Office "12" Open XML 格式文件 (.docx)。  
  
- 適用於您自己應用程式設計的自訂儲存格式。  
  
 基於打包 API，專門<xref:System.Windows.Xps.Packaging.XpsDocument>用於存儲[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]固定內容文檔。 是<xref:System.Windows.Xps.Packaging.XpsDocument>一個自包含文檔，可以在檢視器中打開、顯示在<xref:System.Windows.Controls.DocumentViewer>控制項中、路由到列印周邊同作或直接輸出到與 XPS 相容的印表機。  
  
 以下各節提供有關 提供的<xref:System.IO.Packaging.Package>和<xref:System.Windows.Xps.Packaging.XpsDocument>API 的其他資訊[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
<a name="packages"></a>
### <a name="package-components"></a>封裝元件  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封裝 API 可將應用程式資料和文件組織成單一可攜式單位。 ZIP 檔案就是其中一種最常見的封裝類型，而且是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的預設封裝類型。  <xref:System.IO.Packaging.Package>本身就是一個抽象類別<xref:System.IO.Packaging.ZipPackage>，從中實現使用開放的標準XML和ZIP檔體系結構。  預設情況下<xref:System.IO.Packaging.Package.Open%2A>，該方法<xref:System.IO.Packaging.ZipPackage>用於創建和使用 ZIP 檔。 一個封裝可以包含三種基本項目類型：  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|應用程式內容、資料、文件和資源檔。|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|用於識別、驗證 (Authentication 和 Validation) 的 [X.509 憑證]。|  
|<xref:System.IO.Packaging.PackageRelationship>|與封裝或特定組件相關的新增資訊。|  
  
<a name="PackageParts"></a>
#### <a name="packageparts"></a>PackageParts  
 a（"<xref:System.IO.Packaging.PackagePart>部分"）是一個抽象類別，它引用存儲在 中<xref:System.IO.Packaging.Package>的物件。 在 ZIP 檔案中，封裝組件會對應至儲存在 ZIP 檔案中的個別檔案。  <xref:System.IO.Packaging.ZipPackagePart>為存儲在 中的可序列化物件提供預設實現<xref:System.IO.Packaging.ZipPackage>。  就像檔案系統，封裝中包含的組件會儲存在階層式目錄或「資料夾樣式」的組織中。  使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]打包 API，應用程式可以使用單個 ZIP 檔容器寫入、<xref:System.IO.Packaging.PackagePart>存儲和讀取多個物件。  
  
<a name="PackageDigitalSignatures"></a>
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 為安全，可以<xref:System.IO.Packaging.PackageDigitalSignature>與包中的部件關聯（"數位簽章"）。 A<xref:System.IO.Packaging.PackageDigitalSignature>包含一個 [509]，提供兩個功能：  
  
1. 識別並驗證組件的建立者。  
  
2. 驗證組件未遭修改。  
  
 數位簽章不會防止組件遭到修改，但如果組件有任何改變，對於數位簽章的驗證檢查就會失敗。 應用程式可以做出一些適當的回應，像是防止開啟組件，或通知使用者該組件已遭修改，因此並不安全。  
  
<a name="PackageRelationships"></a>
#### <a name="packagerelationships"></a>PackageRelationships  
 A（"<xref:System.IO.Packaging.PackageRelationship>關係"）提供了一種將附加資訊與包或包中的部件關聯的機制。 關聯性是封裝層級功能，可將其他資訊與組件產生關聯，而不需要修改實際組件內容。 直接將新資料插入組件內容，在許多情況下通常並不可行：  
  
- 不知道組件及其內容結構描述的實際類型。  
  
- 即使知道，內容結構描述也可能不會提供新增資訊的方法。  
  
- 組件可能會進行數位簽署或加密，以免遭到任何修改。  
  
 封裝關聯性提供一個顯而易見的方法，來新增其他資訊，並將此資訊與個別組件或整個封裝產生關聯。 封裝關聯性可用於兩項主要功能：  
  
1. 定義某個組件與另一個組件的相依性關聯性。  
  
2. 定義新增附註或組件之其他相關資料的資訊關聯性。  
  
 A<xref:System.IO.Packaging.PackageRelationship>提供了一種快速、可發現的方法來定義依賴項並添加與包或包整體的一部分關聯的其他資訊。  
  
<a name="Dependency_Relationships"></a>
##### <a name="dependency-relationships"></a>相依性關聯性  
 相依性關聯性可用來描述某個組件與其他組件的相依性。 例如，一個封裝可能包含具有一或多個 \<img> 影像標記的 HTML 組件。 影像標記所參考的影像，就是位於封裝內部或外部 (例如可透過網際網路存取) 的其他組件。 創建與<xref:System.IO.Packaging.PackageRelationship>HTML 檔案關聯的檔使發現和訪問從屬資源變得快速而簡單。 瀏覽器或檢視器應用程式可以直接存取組件關聯性，並立即開始組合相依資源，而不需要知道結構描述或剖析文件。  
  
<a name="Information_Relationships"></a>
##### <a name="information-relationships"></a>資訊關聯性  
 與注釋或注釋類似，還<xref:System.IO.Packaging.PackageRelationship>可用於存儲要與零件關聯的其他類型的資訊，而無需實際修改零件內容本身。  
  
<a name="XPS_Documents"></a>
## <a name="xps-documents"></a>XPS 文件  
 XML 文件規格 （XPS） 文檔是一個包，其中包含一個或多個固定文檔以及呈現所需的所有資源和資訊。  XPS 也是本機 Windows Vista 列印周邊同作檔案格式。  <xref:System.Windows.Xps.Packaging.XpsDocument>存儲在標準 ZIP 資料集中，可以包含 XML 和二進位元件的組合，如圖像和字體檔。 [PackageRelationships](#PackageRelationships) 可用來定義完整呈現文件所需的內容和資源之間的相依性。  該<xref:System.Windows.Xps.Packaging.XpsDocument>設計提供了一個支援多種用途的單一高保真文檔解決方案：  
  
- 將固定格式文件內容和資源當做單一可攜式且容易散發的檔案，進行讀取、寫入及儲存。  
  
- 使用 XPS 檢視器應用程式顯示文檔。  
  
- 以 Windows Vista 的原生列印周邊同作輸出格式輸出文檔。  
  
- 將文檔直接傳送到與 XPS 相容的印表機。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [文本](optimizing-performance-text.md)
- [非固定格式文件概觀](flow-document-overview.md)
- [列印概觀](printing-overview.md)
- [文件序列化與儲存](document-serialization-and-storage.md)
