---
title: "WPF 中的文件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- documents [WPF], packaging
- documents [WPF], text layout
- documents [WPF], XPS
- 'XPS documents [WPF], , '
- documents [WPF], controls
- documents [WPF], types of
- documents [WPF], browser-viewable
ms.assetid: 6e8db7bc-050a-4070-aa72-bb8c46e87ff8
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02f65d68cdaad8824905c4545239f5b607c672d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="documents-in-wpf"></a>WPF 中的文件
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 所提供的各種文件功能可以建立高精確度的內容，此種內容的設計會比在舊版 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 中更加容易存取與閱讀。 除了增強功能和品質，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也針對文件顯示、封裝和安全性提供整合式服務。 本主題提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文件類型和文件封裝的簡介。  
  
  
<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>文件的類型  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 根據文件的預期用途將文件分為兩大類，這兩種文件分類稱為「固定格式文件」與「非固定格式文件」。  
  
 固定格式文件適用於需要精確 [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] 呈現方式的應用程式，與所使用的顯示器或印表機硬體無關。 固定格式文件一般用於桌上出版、文書處理和表單配置，必須嚴格遵循原始頁面設計。 固定格式文件會在其配置中維持內容項目的精確位置，不受使用中的顯示器或列印裝置影響。 例如，在 96 dpi 顯示器上檢視的固定格式文件頁面，不論是輸出到 600 dpi 雷射印表機或輸出到 4800 dpi 相紙輸出機，看起來都完全一樣。 文件品質會充分發揮各裝置的性能，但頁面配置永遠相同。  
  
 相較之下，非固定格式文件的設計用意是為了將檢視及可讀性最佳化；如果容易閱讀是主要的文件使用考量，則最適合使用非固定格式文件。 非固定格式文件並不會設為某種預先定義的配置，而是會根據執行階段變數 (例如視窗大小、裝置解析度和選擇性的使用者喜好設定)，動態調整及自動重排其內容。 網頁即是一個簡單的非固定格式文件範例，其中的頁面內容會動態進行格式化，以符合目前視窗大小。 非固定格式文件會根據執行階段環境，讓使用者擁有最佳的檢視和閱讀體驗。 例如，同一份非固定格式文件在高解析度 19 吋顯示器或小型 2x3 吋 PDA 螢幕上都會動態重新格式化，以獲得最佳可讀性。 此外，非固定格式文件具備許多內建功能，包括搜尋、將可讀性最佳化的檢視模式，以及變更字型大小與外觀的能力。  如需非固定格式文件的說明、範例和深入資訊，請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)。  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>文件控制項和文字配置  
 [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] 提供一組預先建立的控制項，可簡化在應用程式中使用固定格式文件、非固定格式文件和一般文字的作業。  使用支援固定格式文件內容的顯示<xref:System.Windows.Controls.DocumentViewer>控制項。  非固定格式文件內容的顯示支援三個不同的控制項： <xref:System.Windows.Controls.FlowDocumentReader>， <xref:System.Windows.Controls.FlowDocumentPageViewer>，和<xref:System.Windows.Controls.FlowDocumentScrollViewer>其對應至不同的使用者案例 （請參閱下列各節）。  其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項提供簡化的配置，以支援一般文字用途 (請參閱下方的[使用者介面中的文字](#text_in_the_user_interface))。  
  
### <a name="fixed-document-control---documentviewer"></a>固定格式文件控制項 - DocumentViewer  
 <xref:System.Windows.Controls.DocumentViewer>控制項用來顯示<xref:System.Windows.Documents.FixedDocument>內容。 <xref:System.Windows.Controls.DocumentViewer>控制項會提供直覺式使用者介面，支援內建的一般作業包括列印輸出中，將複製到剪貼簿、 縮放及文字搜尋功能。 此控制項可透過常見的捲動機制，來存取多頁內容。 如同所有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項<xref:System.Windows.Controls.DocumentViewer>支援整個或部分的右側，可讓控制項以視覺化方式整合到幾乎任何應用程式或環境。  
  
 <xref:System.Windows.Controls.DocumentViewer>被設計來顯示內容以唯讀方式;編輯或修改的內容不提供，不支援。  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>非固定格式文件控制項  
 **注意︰**如需非固定格式文件功能及其建立方式的詳細資訊，請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)。  
  
 非固定格式文件內容的顯示支援三個控制項： <xref:System.Windows.Controls.FlowDocumentReader>， <xref:System.Windows.Controls.FlowDocumentPageViewer>，和<xref:System.Windows.Controls.FlowDocumentScrollViewer>。  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>包含可讓使用者以動態方式選擇不同的檢視模式，包括單一頁面 （頁面-一次） 檢視模式中，兩個頁面-a-次 （活頁簿讀取格式） 檢視模式，以及連續捲動 （無底邊） 的檢視模式的功能。  如需有關這些檢視模式的詳細資訊，請參閱<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>。  如果您不需要不同的檢視模式之間動態切換<xref:System.Windows.Controls.FlowDocumentPageViewer>和<xref:System.Windows.Controls.FlowDocumentScrollViewer>提供輕量型流程固定的特定檢視模式的內容檢視器。  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer 和 FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>顯示內容頁-一次檢視模式，而<xref:System.Windows.Controls.FlowDocumentScrollViewer>顯示連續捲動模式中的內容。  同時<xref:System.Windows.Controls.FlowDocumentPageViewer>和<xref:System.Windows.Controls.FlowDocumentScrollViewer>會固定為特定檢視模式。 要比較<xref:System.Windows.Controls.FlowDocumentReader>，其中包括功能，可讓使用者以動態方式選擇各種不同的檢視模式之間 (所提供<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>列舉型別)，但要付出正在耗用更多資源<xref:System.Windows.Controls.FlowDocumentPageViewer>或<xref:System.Windows.Controls.FlowDocumentScrollViewer>。  
  
 預設一定會顯示垂直捲軸，而水平捲動則會視需要顯示。 預設值[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]如<xref:System.Windows.Controls.FlowDocumentScrollViewer>不包含的工具列，但是<xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A>屬性可以用來啟用內建工具列。  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>使用者介面中的文字  
 除了將文字新增至文件，您顯然也能在表單等應用程式 UI 中使用文字。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含多個將文字繪製到螢幕的控制項。 每個控制項都是不同案例的目標，且有自己的功能與限制清單。 一般情況下，<xref:System.Windows.Controls.TextBlock>有限的文字支援為必要項，例如簡短句子中時，就應該使用項目[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。 <xref:System.Windows.Controls.Label>需要最少的文字支援時，可以使用。 如需詳細資訊，請參閱 [TextBlock 概觀](../../../../docs/framework/wpf/controls/textblock-overview.md)。  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>文件封裝  
 <xref:System.IO.Packaging> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]提供有效率的方法來組織應用程式資料、 文件內容和存取，可攜性，並可輕鬆地散發簡單的單一容器中的相關的資源。 ZIP 檔案的範例如下<xref:System.IO.Packaging.Package>能夠保留多個物件視為單一單位的型別。 封裝[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]提供預設<xref:System.IO.Packaging.ZipPackage>開放式封裝慣例標準使用 XML 和 ZIP 檔架構而設計的實作。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封裝 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 可讓您輕鬆地建立封裝，以及儲存和存取其中的物件。 物件儲存在<xref:System.IO.Packaging.Package>稱為<xref:System.IO.Packaging.PackagePart>（「 部分 」）。 封裝也可以包含簽署的數位憑證，該憑證可用來識別組件的建立者，以及驗證封裝內容是否未遭修改。  封裝也包含<xref:System.IO.Packaging.PackageRelationship>功能，可讓其他資訊加入至封裝或與特定的組件相關聯，而不需實際修改現有的組件的內容。  封裝服務也支援 [!INCLUDE[TLA#tla_rm](../../../../includes/tlasharptla-rm-md.md)]。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封裝架構是下列幾個重要技術的基礎：  
  
-   符合 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] 的 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 文件。  
  
-   Microsoft Office "12" Open XML 格式文件 (.docx)。  
  
-   適用於您自己應用程式設計的自訂儲存格式。  
  
 根據封裝 Api，<xref:System.Windows.Xps.Packaging.XpsDocument>專為儲存[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]固定內容的文件。 <xref:System.Windows.Xps.Packaging.XpsDocument>是獨立的文件，可以在檢視器中顯示開啟<xref:System.Windows.Controls.DocumentViewer>控制項來列印多工緩衝處理，路由或輸出直接[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-相容的印表機。  
  
 下列各節提供有關的詳細資訊<xref:System.IO.Packaging.Package>和<xref:System.Windows.Xps.Packaging.XpsDocument>[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]隨附[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
<a name="packages"></a>   
### <a name="package-components"></a>封裝元件  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封裝 API 可將應用程式資料和文件組織成單一可攜式單位。 ZIP 檔案就是其中一種最常見的封裝類型，而且是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的預設封裝類型。  <xref:System.IO.Packaging.Package>本身是抽象類別從中<xref:System.IO.Packaging.ZipPackage>使用開放標準 XML 和 ZIP 檔架構實作。  <xref:System.IO.Packaging.Package.Open%2A>方法會使用<xref:System.IO.Packaging.ZipPackage>建立並使用預設的 ZIP 檔案。 一個封裝可以包含三種基本項目類型：  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|應用程式內容、資料、文件和資源檔。|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|用於識別、驗證 (Authentication 和 Validation) 的 [X.509 憑證]。|  
|<xref:System.IO.Packaging.PackageRelationship>|與封裝或特定組件相關的新增資訊。|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 A <xref:System.IO.Packaging.PackagePart> （「 部分 」） 是抽象類別，它是指儲存在物件<xref:System.IO.Packaging.Package>。 在 ZIP 檔案中，封裝組件會對應至儲存在 ZIP 檔案中的個別檔案。  <xref:System.IO.Packaging.ZipPackagePart>提供儲存在可序列化物件的預設實作<xref:System.IO.Packaging.ZipPackage>。  就像檔案系統，封裝中包含的組件會儲存在階層式目錄或「資料夾樣式」的組織中。  使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]封裝 Api，應用程式可以撰寫、 儲存和讀取多個<xref:System.IO.Packaging.PackagePart>物件，使用單一的 ZIP 檔案容器。  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 為了安全性， <xref:System.IO.Packaging.PackageDigitalSignature> （「 數位簽章 」） 可以是在封裝內的組件相關聯。 A<xref:System.IO.Packaging.PackageDigitalSignature>納入 [509] 提供兩個功能：  
  
1.  識別並驗證組件的建立者。  
  
2.  驗證組件未遭修改。  
  
 數位簽章不會防止組件遭到修改，但如果組件有任何改變，對於數位簽章的驗證檢查就會失敗。 應用程式可以做出一些適當的回應，像是防止開啟組件，或通知使用者該組件已遭修改，因此並不安全。  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 A <xref:System.IO.Packaging.PackageRelationship> （「 關係 」） 提供一個機制，將其他資訊與封裝或封裝內的組件產生關聯。 關聯性是封裝層級功能，可將其他資訊與組件產生關聯，而不需要修改實際組件內容。 直接將新資料插入組件內容，在許多情況下通常並不可行：  
  
-   不知道組件及其內容結構描述的實際類型。  
  
-   即使知道，內容結構描述也可能不會提供新增資訊的方法。  
  
-   組件可能會進行數位簽署或加密，以免遭到任何修改。  
  
 封裝關聯性提供一個顯而易見的方法，來新增其他資訊，並將此資訊與個別組件或整個封裝產生關聯。 封裝關聯性可用於兩項主要功能：  
  
1.  定義某個組件與另一個組件的相依性關聯性。  
  
2.  定義新增附註或組件之其他相關資料的資訊關聯性。  
  
 A<xref:System.IO.Packaging.PackageRelationship>提供快速的探索方法，定義相依性，並將與封裝或整個封裝組件相關聯的其他資訊。  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>相依性關聯性  
 相依性關聯性可用來描述某個組件與其他組件的相依性。 例如，一個封裝可能包含具有一或多個 \<img> 影像標記的 HTML 組件。 影像標記所參考的影像，就是位於封裝內部或外部 (例如可透過網際網路存取) 的其他組件。 建立<xref:System.IO.Packaging.PackageRelationship>探索及存取相依的資源快速且輕鬆的 HTML 檔會與相關聯。 瀏覽器或檢視器應用程式可以直接存取組件關聯性，並立即開始組合相依資源，而不需要知道結構描述或剖析文件。  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>資訊關聯性  
 類似的附註或註解，<xref:System.IO.Packaging.PackageRelationship>也可用來儲存其他類型的資訊，而不必實際修改組件內容本身是與組件相關聯。  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>XPS 文件  
 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] 文件是一種封裝，其中包含一或多份固定格式文件，以及進行呈現所需的所有資源和資訊。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 也是原生 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] 列印多工緩衝檔案格式。  <xref:System.Windows.Xps.Packaging.XpsDocument>儲存在標準 ZIP 資料集，且可以包括 XML 和二進位的元件，例如影像和字型檔案的組合。 [PackageRelationships](#PackageRelationships) 可用來定義完整呈現文件所需的內容和資源之間的相依性。  <xref:System.Windows.Xps.Packaging.XpsDocument>設計提供支援多個使用單一的高逼真度的文件方案：  
  
-   將固定格式文件內容和資源當做單一可攜式且容易散發的檔案，進行讀取、寫入及儲存。  
  
-   使用 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 檢視器應用程式顯示文件。  
  
-   以 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] 的原生列印多工緩衝處理輸出格式來輸出文件。  
  
-   將文件直接路由傳送至 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 相容的印表機。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Documents.FixedDocument>  
 <xref:System.Windows.Documents.FlowDocument>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 <xref:System.IO.Packaging.ZipPackage>  
 <xref:System.IO.Packaging.ZipPackagePart>  
 <xref:System.IO.Packaging.PackageRelationship>  
 <xref:System.Windows.Controls.DocumentViewer>  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [文件序列化與儲存](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)
