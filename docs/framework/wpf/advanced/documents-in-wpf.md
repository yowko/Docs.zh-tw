---
title: WPF 中的文件
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
ms.openlocfilehash: e21abca4dd02a849d0240888f831125ab96aa8f1
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393272"
---
# <a name="documents-in-wpf"></a>WPF 中的文件
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供廣泛的檔功能，可讓您建立更容易存取和閱讀的高精確度內容，而不是在舊版的 Windows 中。 除了增強功能和品質，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也針對文件顯示、封裝和安全性提供整合式服務。 本主題提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文件類型和文件封裝的簡介。  

<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>文件的類型  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 根據文件的預期用途將文件分為兩大類，這兩種文件分類稱為「固定格式文件」與「非固定格式文件」。  
  
 固定格式文件適用於需要精確 [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] 呈現方式的應用程式，與所使用的顯示器或印表機硬體無關。 固定格式文件一般用於桌上出版、文書處理和表單配置，必須嚴格遵循原始頁面設計。 固定格式文件會在其配置中維持內容項目的精確位置，不受使用中的顯示器或列印裝置影響。 例如，在 96 dpi 顯示器上檢視的固定格式文件頁面，不論是輸出到 600 dpi 雷射印表機或輸出到 4800 dpi 相紙輸出機，看起來都完全一樣。 文件品質會充分發揮各裝置的性能，但頁面配置永遠相同。  
  
 相較之下，非固定格式文件的設計用意是為了將檢視及可讀性最佳化；如果容易閱讀是主要的文件使用考量，則最適合使用非固定格式文件。 非固定格式文件並不會設為某種預先定義的配置，而是會根據執行階段變數 (例如視窗大小、裝置解析度和選擇性的使用者喜好設定)，動態調整及自動重排其內容。 網頁即是一個簡單的非固定格式文件範例，其中的頁面內容會動態進行格式化，以符合目前視窗大小。 非固定格式文件會根據執行階段環境，讓使用者擁有最佳的檢視和閱讀體驗。 例如，同一份非固定格式文件在高解析度 19 吋顯示器或小型 2x3 吋 PDA 螢幕上都會動態重新格式化，以獲得最佳可讀性。 此外，非固定格式文件具備許多內建功能，包括搜尋、將可讀性最佳化的檢視模式，以及變更字型大小與外觀的能力。  如需非固定格式文件的說明、範例和深入資訊，請參閱[非固定格式文件概觀](flow-document-overview.md)。  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>文件控制項和文字配置  
 .NET Framework 提供一組預先建立的控制項，可簡化在您的應用程式中使用固定檔、非固定格式檔和一般文字。  使用 <xref:System.Windows.Controls.DocumentViewer> 控制項可支援顯示固定的檔內容。  顯示非固定格式檔內容是由三個不同的控制項所支援： <xref:System.Windows.Controls.FlowDocumentReader>、<xref:System.Windows.Controls.FlowDocumentPageViewer> 和 <xref:System.Windows.Controls.FlowDocumentScrollViewer>，其對應至不同的使用者案例（請參閱以下各節）。  其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項提供簡化的配置，以支援一般文字用途 (請參閱下方的[使用者介面中的文字](#text_in_the_user_interface))。  
  
### <a name="fixed-document-control---documentviewer"></a>固定格式文件控制項 - DocumentViewer  
 @No__t-0 控制項的設計目的是要顯示 @no__t 1 內容。 @No__t-0 控制項提供直覺的使用者介面，可針對一般作業（包括列印輸出、複製到剪貼簿、縮放和文字搜尋功能）提供內建支援。 此控制項可透過常見的捲動機制，來存取多頁內容。 就像所有的 @no__t 0 控制項一樣，<xref:System.Windows.Controls.DocumentViewer> 支援完整或部分 restyling，可讓控制項視覺化地整合至幾乎任何應用程式或環境中。  
  
 <xref:System.Windows.Controls.DocumentViewer> 是設計用來以唯讀方式顯示內容;內容的編輯或修改無法使用，且不受支援。  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>非固定格式文件控制項  

> [!NOTE]
> 如需非固定格式檔功能及其建立方式的詳細資訊，請參閱非固定格式[檔總覽](flow-document-overview.md)。  
  
 顯示非固定格式檔內容是由三個控制項所支援： <xref:System.Windows.Controls.FlowDocumentReader>、<xref:System.Windows.Controls.FlowDocumentPageViewer> 和 <xref:System.Windows.Controls.FlowDocumentScrollViewer>。  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>包含的功能可讓使用者在各種不同的視圖模式之間進行動態選擇，包括單頁（一次一頁）的瀏覽模式、兩頁的一次性（書籍閱讀格式）觀賞模式，以及連續滾動（無底邊）查看模式。  如需這些查看模式的詳細資訊， <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>請參閱。  如果您不需要在不同的視圖模式之間進行動態切換的功能<xref:System.Windows.Controls.FlowDocumentPageViewer> ， <xref:System.Windows.Controls.FlowDocumentScrollViewer>並提供在特定的瀏覽模式中固定的較輕量流程內容檢視器。  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer 和 FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>在頁面一次的瀏覽模式中顯示內容，同時<xref:System.Windows.Controls.FlowDocumentScrollViewer>以連續滾動模式顯示內容。  <xref:System.Windows.Controls.FlowDocumentPageViewer> 和<xref:System.Windows.Controls.FlowDocumentScrollViewer>都固定于特定的瀏覽模式。 相較<xref:System.Windows.Controls.FlowDocumentReader>于，其中包含的功能可讓使用者在各種不同的瀏覽模式（由列舉所<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>提供）之間進行動態選擇，代價是比<xref:System.Windows.Controls.FlowDocumentPageViewer>或<xref:System.Windows.Controls.FlowDocumentScrollViewer>更耗費資源的成本。  
  
 預設一定會顯示垂直捲軸，而水平捲動則會視需要顯示。 @No__t-1 的預設 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 不包含工具列;不過，您可以使用 <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> 屬性來啟用內建工具列。  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>使用者介面中的文字  
 除了將文字新增至文件，您顯然也能在表單等應用程式 UI 中使用文字。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含多個將文字繪製到螢幕的控制項。 每個控制項都是不同案例的目標，且有自己的功能與限制清單。 一般而言，需要有限的文字支援時（例如 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中的簡短句子），應該使用 @no__t 0 元素。 當需要最少的文字支援時，可以使用 <xref:System.Windows.Controls.Label>。 如需詳細資訊，請參閱 [TextBlock 概觀](../controls/textblock-overview.md)。  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>文件封裝  
 @No__t-0 Api 提供有效率的方法，在單一容器中組織應用程式資料、檔內容和相關資源，這種方式可輕鬆存取、攜帶和輕鬆散發。 ZIP 檔案是可將多個物件當做單一單位保存的 @no__t 0 類型的範例。 封裝 Api 提供使用開放式封裝慣例標準搭配 XML 和 ZIP 檔案架構設計的預設 @no__t 0 實值。 @No__t 0 封裝 Api 可讓您輕鬆地建立封裝，以及儲存和存取其中的物件。 儲存在 <xref:System.IO.Packaging.Package> 中的物件稱為 <xref:System.IO.Packaging.PackagePart> （"part"）。 封裝也可以包含簽署的數位憑證，該憑證可用來識別組件的建立者，以及驗證封裝內容是否未遭修改。  套件也包含 @no__t 0 的功能，可讓您將其他資訊新增至封裝或與特定元件相關聯，而不需要實際修改現有元件的內容。  封裝服務也支援 Microsoft Windows Rights Management （RM）。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封裝架構是下列幾個重要技術的基礎：  
  
- 符合 XML 紙張規格（XPS）的 XPS 檔。  
  
- Microsoft Office "12" Open XML 格式文件 (.docx)。  
  
- 適用於您自己應用程式設計的自訂儲存格式。  
  
 根據封裝 Api，<xref:System.Windows.Xps.Packaging.XpsDocument> 是特別針對儲存 @no__t 1 固定內容檔所設計。 @No__t-0 是獨立的檔，可以在檢視器中開啟，並顯示在 @no__t 1 控制項中、路由傳送至列印多工緩衝處理，或是直接輸出到與 XPS 相容的印表機。  
  
 下列各節提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所提供的 <xref:System.IO.Packaging.Package> 和 @no__t 1 Api 的其他資訊。  
  
<a name="packages"></a>   
### <a name="package-components"></a>封裝元件  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封裝 API 可將應用程式資料和文件組織成單一可攜式單位。 ZIP 檔案就是其中一種最常見的封裝類型，而且是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的預設封裝類型。  <xref:System.IO.Packaging.Package> 本身是抽象類別，其中 <xref:System.IO.Packaging.ZipPackage> 是使用開放式標準 XML 和 ZIP 檔案架構來執行。  @No__t-0 方法預設會使用 <xref:System.IO.Packaging.ZipPackage> 來建立和使用 ZIP 檔案。 一個封裝可以包含三種基本項目類型：  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|應用程式內容、資料、文件和資源檔。|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|用於識別、驗證 (Authentication 和 Validation) 的 [X.509 憑證]。|  
|<xref:System.IO.Packaging.PackageRelationship>|與封裝或特定組件相關的新增資訊。|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 @No__t-0 （"part"）是一個抽象類別，它會參考儲存在 <xref:System.IO.Packaging.Package> 中的物件。 在 ZIP 檔案中，封裝組件會對應至儲存在 ZIP 檔案中的個別檔案。  <xref:System.IO.Packaging.ZipPackagePart> 會針對儲存在 <xref:System.IO.Packaging.ZipPackage> 中的 serializable 物件提供預設的執行。  就像檔案系統，封裝中包含的組件會儲存在階層式目錄或「資料夾樣式」的組織中。  使用 @no__t 0 封裝 Api，應用程式可以使用單一 ZIP 檔案容器來撰寫、儲存和讀取多個 @no__t 1 的物件。  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 基於安全性，<xref:System.IO.Packaging.PackageDigitalSignature> （「數位簽章」）可以與封裝內的元件產生關聯。 @No__t-0 會併入提供兩個功能的 [509]：  
  
1. 識別並驗證組件的建立者。  
  
2. 驗證組件未遭修改。  
  
 數位簽章不會防止組件遭到修改，但如果組件有任何改變，對於數位簽章的驗證檢查就會失敗。 應用程式可以做出一些適當的回應，像是防止開啟組件，或通知使用者該組件已遭修改，因此並不安全。  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 @No__t-0 （"relationship"）提供了一種機制，可讓其他資訊與封裝或封裝內的元件產生關聯。 關聯性是封裝層級功能，可將其他資訊與組件產生關聯，而不需要修改實際組件內容。 直接將新資料插入組件內容，在許多情況下通常並不可行：  
  
- 不知道組件及其內容結構描述的實際類型。  
  
- 即使知道，內容結構描述也可能不會提供新增資訊的方法。  
  
- 組件可能會進行數位簽署或加密，以免遭到任何修改。  
  
 封裝關聯性提供一個顯而易見的方法，來新增其他資訊，並將此資訊與個別組件或整個封裝產生關聯。 封裝關聯性可用於兩項主要功能：  
  
1. 定義某個組件與另一個組件的相依性關聯性。  
  
2. 定義新增附註或組件之其他相關資料的資訊關聯性。  
  
 @No__t-0 提供快速且可探索的方法來定義相依性，並新增與封裝或整個封裝元件相關聯的其他資訊。  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>相依性關聯性  
 相依性關聯性可用來描述某個組件與其他組件的相依性。 例如，一個封裝可能包含具有一或多個 \<img> 影像標記的 HTML 組件。 影像標記所參考的影像，就是位於封裝內部或外部 (例如可透過網際網路存取) 的其他組件。 建立與 HTML 檔案相關聯的 @no__t 0，可以快速輕鬆地探索和存取相依的資源。 瀏覽器或檢視器應用程式可以直接存取組件關聯性，並立即開始組合相依資源，而不需要知道結構描述或剖析文件。  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>資訊關聯性  
 類似于便箋或批註，<xref:System.IO.Packaging.PackageRelationship> 也可以用來儲存其他類型的資訊，使其與元件相關聯，而不需要實際修改元件內容本身。  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>XPS 文件  
 XML 檔規格（XPS）檔是一種套件，其中包含一或多個固定檔，以及呈現所需的所有資源和資訊。  XPS 也是原生 @no__t 0 列印多工緩衝處理檔案格式。  @No__t-0 會儲存在標準 ZIP 資料集內，而且可以包含 XML 和二進位元件的組合，例如影像和字型檔案。 [PackageRelationships](#PackageRelationships) 可用來定義完整呈現文件所需的內容和資源之間的相依性。  @No__t-0 設計提供單一、高精確度的檔解決方案，可支援多個用途：  
  
- 將固定格式文件內容和資源當做單一可攜式且容易散發的檔案，進行讀取、寫入及儲存。  
  
- 使用 XPS 檢視器應用程式顯示檔。  
  
- 以 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] 的原生列印多工緩衝處理輸出格式來輸出文件。  
  
- 將檔直接路由傳送到與 XPS 相容的印表機。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [Text](optimizing-performance-text.md)
- [非固定格式文件概觀](flow-document-overview.md)
- [列印概觀](printing-overview.md)
- [文件序列化與儲存](document-serialization-and-storage.md)
