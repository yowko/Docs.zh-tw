---
title: 如何：以程式設計方式列印 XPS 檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: a42f9b2101266857e56dee6836f4c3b27b3c6f96
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188321"
---
# <a name="how-to-programmatically-print-xps-files"></a>如何：以程式設計方式列印 XPS 檔
您可以使用一個多載<xref:System.Printing.PrintQueue.AddJob%2A>方法來列印[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]不需開啟的檔案<xref:System.Windows.Controls.PrintDialog>或基本上，任何[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]完全。  
  
 您也可以列印[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]檔案所使用的許多<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>並<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>方法<xref:System.Windows.Xps.XpsDocumentWriter>。 如需詳細資訊，請參閱[列印 XPS 文件](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90))。  
  
 另一種列印[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]是使用<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A>或是<xref:System.Windows.Controls.PrintDialog.PrintVisual%2A>方法<xref:System.Windows.Controls.PrintDialog>控制項。 請參閱[叫用列印對話方塊](how-to-invoke-a-print-dialog.md)。  
  
## <a name="example"></a>範例  
 使用三個參數的主要步驟<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>方法如下所示。 下列範例會提供詳細資料。  
  
1.  判斷印表機是否為 XPSDrv 印表機。 (如需 XPSDrv 的詳細資訊，請參閱[列印概觀](printing-overview.md)。)  
  
2.  如果印表機不是 XPSDrv 印表機，將執行緒的 Apartment 設定為單一執行緒。  
  
3.  將列印伺服器與列印佇列物件具現化。  
  
4.  呼叫方法，指定作業名稱、 要列印的檔案和<xref:System.Boolean>旗標，指出印表機是否為 XPSDrv 印表機。  
  
 下列範例示範如何批次列印目錄中的所有 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 檔案。 雖然應用程式會提示使用者指定的目錄，包含三個參數<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>方法不需要[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。 它可以使用於任何程式碼路徑，其中包含您可以傳遞至的 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 檔案名稱和路徑。  
  
 包含三個參數<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>多載<xref:System.Printing.PrintQueue.AddJob%2A>必須在單一執行緒 apartment 中執行每當<xref:System.Boolean>參數是`false`，它必須是在使用非 XPSDrv 印表機時。 不過，[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] 的預設 Apartment 狀態為多執行緒。 必須還原此預設值，因為此範例採用非 XPSDrv 印表機。  
  
 變更預設值的方式有兩種。 其中一種方式是直接加入<xref:System.STAThreadAttribute>(也就是"`[System.STAThreadAttribute()]`") 正上方的應用程式的第一行`Main`方法 (通常是"`static void Main(string[] args)`」)。 不過，許多應用程式，需要`Main`方法具有多執行緒的 apartment 狀態，因此沒有第二個方法： put 呼叫<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>在個別執行緒的 apartment 狀態會設為<xref:System.Threading.ApartmentState.STA>使用<xref:System.Threading.Thread.SetApartmentState%2A>。 下列範例使用此第二種技術。  
  
 因此，此範例一開始具現化<xref:System.Threading.Thread>物件，並將其傳遞**PrintXPS**方法，以作為<xref:System.Threading.ThreadStart>參數。 (**PrintXPS** 方法稍後會定義在範例中。)接下來執行緒會設定為單一執行緒 Apartment。 `Main` 方法唯一剩餘的程式碼會啟動新的執行緒。  
  
 範例的實質內容是在 `static`**BatchXPSPrinter.PrintXPS** 方法中。 建立列印伺服器和佇列之後，此方法會提示使用者提供一個包含 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 檔案的目錄。 驗證目錄是否存在以及是否有之後\*.xps 檔案中，方法會將每個這類檔案加入到列印佇列。 此範例假設印表機是非 XPSDrv，因此我們傳遞`false`的最後一個參數以<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>方法。 基於這個理由，此方法會先驗證檔案中的 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 標記，再嘗試將它轉換成印表機的頁面描述語言。 如果驗證失敗，則會擲回例外狀況。 範例程式碼會攔截例外狀況、通知使用者，然後繼續處理下一個 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 檔案。  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 如果您使用 XPSDrv 印表機，則可以將最終參數設定為 `true`。 在此情況下，因為 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 是印表機的頁面描述語言，所以此方法會將檔案傳送至印表機，而不需要進行驗證，或將它轉換成另一種頁面描述語言。 如果您不確定在設計階段是否應用程式將會使用 XPSDrv 印表機，您可以修改應用程式，讓它讀取<xref:System.Printing.PrintQueue.IsXpsDevice%2A>屬性和根據它所找到的分支。  
  
 因為有一開始可幾部 XPSDrv 印表機立即發行後[!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]和 Microsoft.NET Framework 中，您可能需要偽裝成 XPSDrv 印表機非 XPSDrv 印表機。 若要這樣做，請將 Pipelineconfig.xml 新增至執行您應用程式之電腦的下列登錄機碼中的檔案清單︰  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\*\<PseudoXPSPrinter>* \DependentFiles  
  
 其中 *\<PseudoXPSPrinter>* 是任何列印佇列。 電腦之後必須重新開機。  
  
 此偽裝可讓您傳遞`true`做為最後的參數<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>而不會造成例外狀況，但由於 *\<Pseudoxpsprinter> >* 並非真正的 XPSDrv 印表機，只是記憶體回收會列印。  
  
 **附註**為了簡單起見，上述範例中使用的目前狀態\*.xps 副檔名的檔案來測試[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]。 不過，[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 檔案不一定要有此副檔名。 [isXPS.exe (isXPS 一致性工具)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) 是一種測試檔案之 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 有效性的方法。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.AddJob%2A>  
 <xref:System.Threading.ApartmentState>  
 <xref:System.STAThreadAttribute>  
 [XPS](https://www.microsoft.com/xps)  
 [列印 XPS 文件](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90))  
 [Managed 和 Unmanaged 執行緒處理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))  
 [isXPS.exe (isXPS 一致性工具)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100))  
 [WPF 中的文件](documents-in-wpf.md)  
 [列印概觀](printing-overview.md)
