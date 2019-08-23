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
ms.openlocfilehash: 43b0ddc8f683e7069207bbb1c47af73976bc4a5a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958550"
---
# <a name="printing-overview"></a>列印概觀
透過 Microsoft .NET Framework, 使用 Windows Presentation Foundation (WPF) 的應用程式開發人員有一組豐富的列印和列印系統管理 Api。 藉由 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]，某些列印系統增強功能也可供建立 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 應用程式的開發人員和使用 Unmanaged 程式碼的開發人員使用。 這項新功能的核心是新的 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] 檔案格式和 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 列印路徑。  
  
 此主題包括下列各節。  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>關於 XPS  
 XPS 是一種電子檔案格式, 也就是多工緩衝處理檔案格式和分頁描述語言。 這是一種開放檔案格式, [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]其使用、開放封裝慣例 (OPC) 以及其他業界標準來建立跨平臺檔。 XPS 簡化了建立、共用、列印、查看和封存數位檔的程式。 如需有關 XPS 的其他資訊, 請參閱[Xps 檔](/windows/desktop/printdocs/documents)。  
  
 以程式設計[方式列印 xps](how-to-programmatically-print-xps-files.md)檔案時, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]有數種用來列印 xps 內容的技巧。 在檢閱本主題所包含內容期間，您會發現參考這些範例相當有用。 (非受控程式碼開發人員應該會看到[MXDC_ESCAPE 函數](/windows/desktop/printdocs/mxdc-escape)的檔。 Windows Forms 開發人員必須在<xref:System.Drawing.Printing>命名空間中使用不支援完整[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]列印路徑的 API, 但支援混合式 GDI 到 XPS 列印路徑。 請參閱下方的**列印路徑架構**)。  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>XPS 列印路徑  
 XML 檔規格 (XPS) 列印路徑是新的 Windows 功能, 可重新定義在 Windows 應用程式中處理列印的方式。 因為[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]可以取代檔呈現語言 (例如 RTF)、列印多工緩衝處理器格式 (例如 WMF), 以及分頁描述語言 (例如 PCL 或 Postscript); 新的列印路徑會維護從應用程式發行到的 XPS 格式。列印驅動程式或裝置中的最後處理。  
  
 Xps 列印路徑是以 xps 印表機驅動程式模型 (XPSDrv) 為基礎, 可為開發人員[!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)]提供數個優點, 例如列印、改良的色彩支援, 以及大幅改進的列印效能。 (如需 XPSDrv 的詳細資訊, 請參閱[Windows 驅動程式套件檔](/windows-hardware/drivers/)。)  
  
 XPS 檔列印多工緩衝處理器的操作, 基本上與舊版 Windows 相同。 不過, 它已經過增強, 可支援現有的 GDI 列印路徑以外的 XPS 列印路徑。 新的列印路徑原本就會使用 XPS 多工緩衝處理檔案。 雖然為舊版 Windows 撰寫的使用者模式印表機驅動程式仍可繼續使用, 但還是需要 XPS 印表機驅動程式 (XPSDrv) 才能使用 XPS 列印路徑。  
  
 XPS 列印路徑的優點很重要, 其中包括:  
  
- [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)] 列印支援  
  
- 進階色彩設定檔的原生支援，其中包含每個通道 32 位元 (bpc)、CMYK、具名色彩、n-inks 和透明及漸層效果的原生支援。  
  
- 改善 .NET Framework 和[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]應用程式的列印效能。  
  
- 業界標準 XPS 格式。  
  
 在基本的列印案例中, 有一個簡單且直覺的 API 可供使用者介面、設定和作業提交的單一進入點使用。 進階案例中，對於 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 自訂 (或根本沒有 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)])、同步或非同步列印及批次列印功能，加入額外支援。 這兩個選項都提供完整或部分信任模式中的列印支援。  
  
 XPS 是以擴充性為考慮而設計的。 藉由使用擴充性架構, 可以透過模組化方式將特性和功能新增至 XPS。 擴充性功能包括：  
  
- 列印結構描述。 會定期更新公用結構描述，並讓裝置功能可快速擴充。 (請參閱下方的 **PrintTicket 和 PrintCapabilities**)。  
  
- 可擴充的篩選管線。 XPS 印表機驅動程式 (XPSDrv) 篩選器管線的設計, 是為了啟用 XPS 檔的直接與可調整列印。 如需詳細資訊, 請參閱[XPSDrv 印表機驅動程式](/windows-hardware/drivers/print/xpsdrv-printer-drivers)。 
  
### <a name="print-path-architecture"></a>列印路徑架構  
 雖然和[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] .NET Framework 的應用程式都支援[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] xps, 而 Windows Forms 應用程式會使用 GDI 進行 xps 轉換, 以便為 xps 印表機驅動程式 (XPSDrv) 建立 xps 格式的內容。 這些應用程式不需要使用 XPS 列印路徑, 而且可以繼續使用增強型中繼檔 (EMF) 為基礎的列印。 不過, 大部分的 XPS 功能和增強僅適用于以 XPS 列印路徑為目標的應用程式。  
  
 為了啟用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]和 Windows Forms 應用程式使用 XPSDrv 型印表機, XPS 印表機驅動程式 (XPSDrv) 支援將 GDI 轉換成 XPS 格式。 XPSDrv 模型也提供 XPS 到 GDI 格式的轉換器, 讓[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]應用程式可以列印[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]檔。 針對[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式, 每當寫入作業的目標列印佇列沒有 XPSDrv 驅動<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>程式時, 就<xref:System.Windows.Xps.XpsDocumentWriter>會透過類別的和<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>方法, 自動完成 XPS 到 GDI 格式的轉換。 (Windows Forms 應用程式無法[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]列印檔案)。  
  
 下圖說明列印子系統, 並定義所提供[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]的部分, 以及軟體和硬體廠商所定義的部分:  
  
 ![螢幕擷取畫面: 顯示 XPS 列印系統。](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>基本 XPS 列印  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]定義基本和先進的 API。 對於不需要大量列印自訂或存取完整 XPS 功能集的應用程式, 可以使用基本列印支援。 基本列印支援由需要最少組態的列印對話方塊控制項公開，並具有類似 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的功能。 許多 XPS 功能都可以使用這個簡化的列印模型來取得。  
  
#### <a name="printdialog"></a>PrintDialog  
 控制項提供[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、設定和 XPS 工作提交的單一進入點。 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> 如需如何具現化及使用控制項的相關資訊，請參閱[叫用列印對話方塊](how-to-invoke-a-print-dialog.md)。  
  
### <a name="advanced-xps-printing"></a>進階的 XPS 列印  
 若要存取一組完整的 XPS 功能, 必須使用 advanced print API。 下面會更詳細說明數個相關的 API。 如需 XPS 列印路徑 api 的完整清單, 請參閱<xref:System.Windows.Xps>和<xref:System.Printing>命名空間參考。  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket 和 PrintCapabilities  
 <xref:System.Printing.PrintTicket> 和<xref:System.Printing.PrintCapabilities>類別是 advanced XPS 功能的基礎。 這兩種類型的物件都是列印導向功能的 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 格式化結構，例如定序、雙面列印、裝訂等等。列印的結構描述會定義這些結構。 <xref:System.Printing.PrintTicket> 會指示印表機該如何處理列印工作。 <xref:System.Printing.PrintCapabilities> 類別會定義印表機的功能。 藉由查詢印表機的功能，可以建立 <xref:System.Printing.PrintTicket> 來完整利用印表機支援的功能。 同樣地，您也可避免不支援的功能。  
  
 下列範例示範如何查詢印表機的 <xref:System.Printing.PrintCapabilities>，並使用程式碼建立 <xref:System.Printing.PrintTicket>。  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer 和 PrintQueue  
 <xref:System.Printing.PrintServer> 類別代表網路列印伺服器，且 <xref:System.Printing.PrintQueue> 類別代表印表機以及相關聯的輸出工作佇列。 這些 Api 一起使用, 可讓您進行伺服器列印工作的先進管理。 <xref:System.Printing.PrintServer> 或其中一個衍生的類別，會用來管理 <xref:System.Printing.PrintQueue>。 <xref:System.Printing.PrintQueue.AddJob%2A> 方法會用來將新的列印工作插入佇列。  
  
 下列範例示範如何建立 <xref:System.Printing.LocalPrintServer> 及使用程式碼存取其預設的 <xref:System.Printing.PrintQueue>。  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 <xref:System.Printing.PrintQueue>具有許多和方法<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>的,可用來將<xref:System.Windows.Xps.XpsDocumentWriter>XPS <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>檔寫入。 例如, <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29>方法用來以<xref:System.Printing.PrintTicket>同步方式輸出 XPS 檔。 方法是用來以<xref:System.Printing.PrintTicket>非同步方式輸出 XPS 檔。 <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29>  
  
 下列範例示範如何使用程式碼建立 <xref:System.Windows.Xps.XpsDocumentWriter>。  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> 方法也會提供列印的方式。 請參閱[以程式設計方式列印 XPS 檔](how-to-programmatically-print-xps-files.md)。 。  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>GDI 列印路徑  
 雖然[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式原本就支援 xps 列印路徑[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] , 而 Windows Forms 應用程式也可以利用某些 xps 功能。 XPS 印表機驅動程式 (XPSDrv) 可以將 GDI 型輸出轉換成 XPS 格式。 針對先進的案例, 使用[MICROSOFT XPS 檔轉換子 (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)可支援內容的自訂轉換。 同樣地[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , 應用程式也可以藉由呼叫<xref:System.Windows.Xps.XpsDocumentWriter>類別的其中一個<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>或<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>方法, 並指定非 XpsDrv 印表機做為目標列印佇列, 輸出至 GDI 列印路徑。  

對於不需要 XPS 功能或支援的應用程式, 目前的 GDI 列印路徑會保持不變。  
  
- 如需 GDI 列印路徑和各種 XPS 轉換選項的其他參考資料, 請參閱[MICROSOFT XPS 檔轉換器 (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)和[XPSDrv 印表機驅動程式](/windows-hardware/drivers/print/xpsdrv-printer-drivers)。  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>XPSDrv 驅動程式模型  
 XPS 列印路徑可在列印到啟用 XPS 的印表機或驅動程式時, 使用 XPS 作為原生列印多工緩衝處理格式, 藉此改善多工緩衝處理器的效率。 簡化的多工緩衝處理常式不需要產生中繼多工緩衝檔案 (例如 EMF 資料檔案), 就能將檔進行多工緩衝處理。 透過較小的多工緩衝處理檔案大小, XPS 列印路徑可以減少網路流量並改善列印效能。  
  
 EMF 是一種關閉的格式, 代表應用程式輸出, 做為轉譯服務的 GDI 的一系列呼叫。 與 EMF 不同的是, XPS 多工緩衝處理格式代表實際的檔, 而不需要在輸出至 XPS 型印表機驅動程式 (XPSDrv) 時進一步轉譯。 驅動程式可以直接在格式中的資料上運作。 當您使用 EMF 檔案和以 GDI 為基礎的列印驅動程式時, 這項功能可排除所需的資料和色彩空間轉換。  
  
 當您使用以 XPS 印表機驅動程式 (XPSDrv) 為目標的 XPS 檔 (相較于其 EMF 對應專案) 時, 多工緩衝處理檔案大小通常會降低不過, 有一些例外狀況:  
  
- 非常複雜、多層或無效率寫入的向量圖形可能大於相同圖形的點陣圖版本。  
  
- 供螢幕顯示之用，XPS 檔內嵌裝置字型，以及以電腦為基礎的字型；而 GDI 多工緩衝處理檔案則不會內嵌裝置字型。 但是這兩種字型為部分內嵌的字型 (如下所示)，而且印表機驅動程式可以移除裝置字型，然後再將檔案傳輸至印表機。  
  
 多工緩衝處理大小縮減會透過數種機制執行：  
  
- **字型部分內嵌**。 只有在實際檔中使用的字元會儲存在 XPS 檔案中。  
  
- **進階圖形支援**。 透明及漸層效果基本類型的原生支援可避免 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 文件中內容的點陣化。  
  
- **識別通用資源**。 多次使用的資源 (例如代表公司標誌的影像) 會被視為共用資源，並只會載入一次。  
  
- **ZIP 壓縮**。 所有 XPS 檔都使用 ZIP 壓縮。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [HOW-TO 主題](printing-how-to-topics.md)
- [WPF 中的文件](documents-in-wpf.md)
- [XPS 檔](/windows/desktop/printdocs/documents)
- [文件序列化與儲存](document-serialization-and-storage.md)
- [Microsoft XPS 檔轉換子 (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
