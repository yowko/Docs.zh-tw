---
title: 列印概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print path [WPF], XPS
- printers [WPF], XPSDrv-based
- printing [WPF]
- PrintQueue class PrintServer class [WPF]
- XML Paper Specification (XPS) file format
- XPS (XML Paper Specification) file format
- XPSDrv-based printers
- GDI print path [WPF]
ms.assetid: 0de8ac41-9aa6-413d-a121-7aa6f41539b1
ms.openlocfilehash: 902d51341850b5245b9fa6410b1954b2ab373bbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187206"
---
# <a name="printing-overview"></a>列印概觀
使用 Microsoft .NET 框架，使用 Windows 演示基礎 （WPF） 的應用程式開發人員具有一套豐富的新列印和列印系統管理 API。 使用 Windows Vista，這些列印系統增強功能中的一些也可用於創建 Windows 表單應用程式的開發人員和使用非託管代碼的開發人員。 此新功能的核心是新的 XML 文件規格 （XPS） 檔案格式和 XPS 列印路徑。  
  
 本主題包含下列各節。  
  
<a name="introduction_to_XPS"></a>
## <a name="about-xps"></a>關於 XPS  
 XPS 是一種電子文檔格式、周邊同作檔案格式和分頁描述語言。 它是一種開放文檔格式，使用 XML、開放打包約定 （OPC） 和其他行業標準來創建跨平臺文檔。 XPS 簡化了數位文檔的創建、共用、列印、查看和存檔過程。 有關 XPS 的其他資訊，請參閱[XPS 文檔](/windows/desktop/printdocs/documents)。  
  
 使用 WPF 列印基於 XPS 的內容的幾種技術在[程式設計列印 XPS 檔中](how-to-programmatically-print-xps-files.md)進行了演示。 在檢閱本主題所包含內容期間，您會發現參考這些範例相當有用。 （非託管代碼開發人員應查看[MXDC_ESCAPE函數](/windows/desktop/printdocs/mxdc-escape)的文檔。 Windows 表單開發人員必須在不支援完整<xref:System.Drawing.Printing>XPS 列印路徑但支援混合 GDI 到 XPS 列印路徑的命名空間中使用 API。 請參閱下方的**列印路徑架構**)。  
  
<a name="XPS_print_path_intro"></a>
## <a name="xps-print-path"></a>XPS 列印路徑  
 XML 文件規格 （XPS） 列印路徑是一項新 Windows 功能，可重新定義在 Windows 應用程式中處理列印的方式。 因為 XPS 可以替換文檔演示語言（如 RTF）、列印幕後列印器格式（如 WMF）和分頁描述語言（如 PCL 或後記）;新的列印路徑在列印驅動程式或設備中維護從應用程式發佈到最終處理的 XPS 格式。  
  
 XPS 列印路徑基於 XPS 印表機驅動程式模型 （XPSDrv） 構建，它為開發人員提供了多種好處，例如"您所看到的就是您得到的"（WYSIWYG）列印、改進了顏色支援以及顯著提高了列印性能。 （有關 XPSDrv 的更多資訊，請參閱[Windows 驅動程式工具組文檔](/windows-hardware/drivers/)。  
  
 XPS 文檔的列印幕後程式的操作與早期版本的 Windows 基本相同。 但是，除了現有的 GDI 列印路徑之外，它還增強了 XPS 列印路徑。 新的列印路徑本機使用 XPS 周邊同作檔。 雖然為早期版本的 Windows 編寫的使用者模式印表機驅動程式將繼續工作，但 XPS 印表機驅動程式 （XPSDrv） 需要一個才能使用 XPS 列印路徑。  
  
 XPS 列印路徑的優勢非常重要，包括：  
  
- 威西威格列印支援  
  
- 進階色彩設定檔的原生支援，其中包含每個通道 32 位元 (bpc)、CMYK、具名色彩、n-inks 和透明及漸層效果的原生支援。  
  
- 提高了 .NET 框架和基於 Win32 的應用程式的列印性能。  
  
- 行業標準 XPS 格式。  
  
 對於基本列印方案，提供簡單直觀的 API，並帶有一個進入點，用於使用者介面、配置和作業提交。 進階案例中，對於 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 自訂 (或根本沒有 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)])、同步或非同步列印及批次列印功能，加入額外支援。 這兩個選項都提供完整或部分信任模式中的列印支援。  
  
 XPS 的設計考慮到了可擴充性。 通過使用可擴充性框架，可以模組化地將特性和功能添加到 XPS 中。 擴充性功能包括：  
  
- 列印結構描述。 會定期更新公用結構描述，並讓裝置功能可快速擴充。 (請參閱下方的 **PrintTicket 和 PrintCapabilities**)。  
  
- 可擴充的篩選管線。 XPS 印表機驅動程式 （XPSDrv） 過濾管道旨在支援直接和可擴展地列印 XPS 文檔。 有關詳細資訊，請參閱[XPSDrv 印表機驅動程式](/windows-hardware/drivers/print/xpsdrv-printer-drivers)。
  
### <a name="print-path-architecture"></a>列印路徑架構  
 雖然 Win32 和 .NET 框架應用程式都支援 XPS，但 Win32 和 Windows 表單應用程式使用 GDI 到 XPS 轉換，以便為 XPS 印表機驅動程式 （XPSDrv） 創建 XPS 格式化的內容。 這些應用程式不需要使用 XPS 列印路徑，並且可以繼續使用基於增強的中繼檔 （EMF） 列印。 但是，大多數 XPS 功能和增強功能僅對面向 XPS 列印路徑的應用程式可用。  
  
 為了啟用 Win32 和 Windows 表單應用程式使用基於 XPSDrv 的印表機，XPS 印表機驅動程式 （XPSDrv） 支援將 GDI 轉換為 XPS 格式。 XPSDrv 型號還為 XPS 到 GDI 格式提供了轉換器，以便 Win32 應用程式可以列印 XPS 文檔。 對於 WPF 應用程式，只要寫入操作的目標列印佇列沒有 XPSDrv<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>驅動程式，XPS 格式轉換為 GDI 格式由<xref:System.Windows.Xps.XpsDocumentWriter>類<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>和方法自動完成。 （Windows 表單應用程式無法列印 XPS 文檔。  
  
 下圖描述了列印子系統，並定義了 Microsoft 提供的部分以及軟體和硬體供應商定義的部分：  
  
 ![螢幕截圖顯示了 XPS 列印系統。](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>基本 XPS 列印  
 WPF 同時定義基本和高級 API。 對於不需要大量列印自訂或訪問完整 XPS 功能集的應用程式，可提供基本列印支援。 基本列印支援由需要最少組態的列印對話方塊控制項公開，並具有類似 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的功能。 許多 XPS 功能都可用於使用此簡化的列印模型。  
  
#### <a name="printdialog"></a>PrintDialog  
 該<xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>控制項為[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、配置和 XPS 作業提交提供單個進入點。 如需如何具現化及使用控制項的相關資訊，請參閱[叫用列印對話方塊](how-to-invoke-a-print-dialog.md)。  
  
### <a name="advanced-xps-printing"></a>進階的 XPS 列印  
 要訪問完整的 XPS 功能集，必須使用高級列印 API。 下面將更詳細地介紹幾個相關的 API。 有關 XPS 列印路徑 API 的完整清單，請參閱<xref:System.Windows.Xps><xref:System.Printing>和 命名空間引用。  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket 和 PrintCapabilities  
 <xref:System.Printing.PrintTicket>和<xref:System.Printing.PrintCapabilities>類是高級 XPS 功能的基礎。 這兩種類型的物件都是面向列印的功能（如排序、雙面列印、裝訂等）的 XML 格式結構。這些結構由列印架構定義。 <xref:System.Printing.PrintTicket> 會指示印表機該如何處理列印工作。 <xref:System.Printing.PrintCapabilities> 類別會定義印表機的功能。 藉由查詢印表機的功能，可以建立 <xref:System.Printing.PrintTicket> 來完整利用印表機支援的功能。 同樣地，您也可避免不支援的功能。  
  
 下列範例示範如何查詢印表機的 <xref:System.Printing.PrintCapabilities>，並使用程式碼建立 <xref:System.Printing.PrintTicket>。  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer 和 PrintQueue  
 <xref:System.Printing.PrintServer> 類別代表網路列印伺服器，且 <xref:System.Printing.PrintQueue> 類別代表印表機以及相關聯的輸出工作佇列。 總之，這些 API 允許對伺服器的列印工作進行高級管理。 <xref:System.Printing.PrintServer> 或其中一個衍生的類別，會用來管理 <xref:System.Printing.PrintQueue>。 <xref:System.Printing.PrintQueue.AddJob%2A> 方法會用來將新的列印工作插入佇列。  
  
 下列範例示範如何建立 <xref:System.Printing.LocalPrintServer> 及使用程式碼存取其預設的 <xref:System.Printing.PrintQueue>。  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 A<xref:System.Windows.Xps.XpsDocumentWriter>及其許多<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>和<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>方法用於將 XPS 文檔寫入 。 <xref:System.Printing.PrintQueue> 例如，<xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29>該方法用於輸出 XPS 文檔並<xref:System.Printing.PrintTicket>同步輸出。 該方法<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29>用於輸出 XPS 文檔並<xref:System.Printing.PrintTicket>非同步輸出。  
  
 下列範例示範如何使用程式碼建立 <xref:System.Windows.Xps.XpsDocumentWriter>。  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> 方法也會提供列印的方式。 請參閱[以程式設計方式列印 XPS 檔](how-to-programmatically-print-xps-files.md)。 。  
  
<a name="GDI_Print_Path_intro"></a>
## <a name="gdi-print-path"></a>GDI 列印路徑  
 雖然 WPF 應用程式本機支援 XPS 列印路徑，但 Win32 和 Windows 表單應用程式也可以利用某些 XPS 功能。 XPS 印表機驅動程式 （XPSDrv） 可將基於 GDI 的輸出轉換為 XPS 格式。 對於高級方案，支援使用[Microsoft XPS 文檔轉換器 （MXDC）](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)自訂內容轉換。 同樣，WPF 應用程式還可以通過調用<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A><xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A><xref:System.Windows.Xps.XpsDocumentWriter>類的或方法之一併將非 XpsDrv 印表機指定為目標列印佇列，輸出到 GDI 列印路徑。  

對於不需要 XPS 功能或支援的應用程式，當前 GDI 列印路徑保持不變。  
  
- 有關 GDI 列印路徑和各種 XPS 轉換選項的其他參考資料，請參閱[Microsoft XPS 文檔轉換器 （MXDC）](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)和[XPSDrv 印表機驅動程式](/windows-hardware/drivers/print/xpsdrv-printer-drivers)。  
  
<a name="XPS_Driver_Model_intro"></a>
## <a name="xpsdrv-driver-model"></a>XPSDrv 驅動程式模型  
 在列印到啟用 XPS 的印表機或驅動程式時，XPS 列印路徑使用 XPS 作為本機列印周邊同作格式，從而提高了幕後程式的效率。 簡化的幕後列印過程消除了在文檔後臺化之前生成中間周邊同作檔（如 EMF 資料檔案）的需要。 通過更小的周邊同作檔案大小，XPS 列印路徑可以減少網路流量並提高列印性能。  
  
 EMF 是一種封閉格式，表示應用程式輸出為一系列對 GDI 的調用，用於呈現服務。 與 EMF 不同，XPS 周邊同作格式表示實際文檔，無需在輸出到基於 XPS 的印表機驅動程式 （XPSDrv） 時需要進一步解釋。 驅動程式可以直接在格式中的資料上運作。 此功能消除了使用 EMF 檔和基於 GDI 的列印驅動程式所需的資料和色彩空間轉換。  
  
 與 EMF 等效項相比，當您使用針對 XPS 印表機驅動程式 （XPSDrv） 的 XPS 文檔時，Spool 檔案大小通常會減小;但是，也有例外：  
  
- 非常複雜、多層或無效率寫入的向量圖形可能大於相同圖形的點陣圖版本。  
  
- 供螢幕顯示之用，XPS 檔內嵌裝置字型，以及以電腦為基礎的字型；而 GDI 多工緩衝處理檔案則不會內嵌裝置字型。 但是這兩種字型為部分內嵌的字型 (如下所示)，而且印表機驅動程式可以移除裝置字型，然後再將檔案傳輸至印表機。  
  
 多工緩衝處理大小縮減會透過數種機制執行：  
  
- **字型部分內嵌**。 XPS 檔中僅存儲實際文檔中使用的字元。  
  
- **進階圖形支援**。 對透明度和梯度基元的本機支援可避免 XPS 文檔中內容的柵格化。  
  
- **識別通用資源**。 多次使用的資源 (例如代表公司標誌的影像) 會被視為共用資源，並只會載入一次。  
  
- **ZIP 壓縮**。 所有 XPS 文檔都使用 ZIP 壓縮。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [如何使用主題](printing-how-to-topics.md)
- [WPF 中的文件](documents-in-wpf.md)
- [XPS 文件](/windows/desktop/printdocs/documents)
- [文件序列化與儲存](document-serialization-and-storage.md)
- [微軟XPS文檔轉換器（MXDC）](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
