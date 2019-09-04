---
title: 作法：以程式設計方式列印 XPS 檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: 5571544284326fa7ce26382711f696734a166df5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254099"
---
# <a name="how-to-programmatically-print-xps-files"></a>作法：以程式設計方式列印 XPS 檔
您可以使用方法的<xref:System.Printing.PrintQueue.AddJob%2A>其中一個多載來列印 XML 檔規格 (XPS) 檔案, 而不需要開啟或, 其中任何[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]一<xref:System.Windows.Controls.PrintDialog>項。  
  
 您也可以使用多個<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A?displayProperty=nameWithType>和<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A?displayProperty=nameWithType>方法來列印 XPS 檔案。 如需詳細資訊, 請參閱[列印 XPS 檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90))。  
  
 列印 XPS 的另一種方式是使用<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A?displayProperty=nameWithType>或<xref:System.Windows.Controls.PrintDialog.PrintVisual%2A?displayProperty=nameWithType>方法。 請參閱[叫用列印對話方塊](how-to-invoke-a-print-dialog.md)。  
  
## <a name="example"></a>範例  
 使用三個參數<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>方法的主要步驟如下所示。 下列範例會提供詳細資料。  
  
1. 判斷印表機是否為 XPSDrv 印表機。 (如需 XPSDrv 的詳細資訊，請參閱[列印概觀](printing-overview.md)。)  
  
2. 如果印表機不是 XPSDrv 印表機，將執行緒的 Apartment 設定為單一執行緒。  
  
3. 將列印伺服器與列印佇列物件具現化。  
  
4. 呼叫方法, 指定工作名稱、要列印的檔案, 以及<xref:System.Boolean>指出印表機是否為 XPSDrv 印表機的旗標。  
  
 下列範例顯示如何批次處理目錄中的所有 XPS 檔案。 雖然應用程式會提示使用者指定目錄, 但是三個參數<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>的方法並不[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]需要。 它可以用於您擁有 XPS 檔案名和路徑的任何程式碼路徑中, 而您可以將其傳遞給它。  
  
 當<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> <xref:System.Boolean>參數<xref:System.Printing.PrintQueue.AddJob%2A> 為`false`時, 的三參數多載必須在單一線程中執行, 這在使用非 XPSDrv 印表機時必須是。 不過, .NET 的預設單元狀態為多執行緒。 必須還原此預設值，因為此範例採用非 XPSDrv 印表機。  
  
 變更預設值的方式有兩種。 其中一種方式是直接在<xref:System.STAThreadAttribute>應用程式`Main`方法的第`[System.STAThreadAttribute()]`一行 (通常是 "`static void Main(string[] args)`") 正上方加入 (也就是 "")。 不過, 許多應用程式都需要`Main`方法具有多執行緒的單元狀態, 因此有第二個方法: 將的<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>呼叫放入另一個執行緒, 其的單元<xref:System.Threading.Thread.SetApartmentState%2A>狀態設定為<xref:System.Threading.ApartmentState.STA> 。 下列範例使用此第二種技術。  
  
 因此, 此範例一<xref:System.Threading.Thread>開始會先具現化物件, 並傳遞**PrintXPS**方法<xref:System.Threading.ThreadStart>做為參數。 (**PrintXPS** 方法稍後會定義在範例中。)接下來執行緒會設定為單一執行緒 Apartment。 `Main` 方法唯一剩餘的程式碼會啟動新的執行緒。  
  
 範例的實質內容是在 `static`**BatchXPSPrinter.PrintXPS** 方法中。 建立列印伺服器和佇列之後, 方法會提示使用者輸入包含 XPS 檔案的目錄。 在驗證目錄是否存在, 以及其中是否有 .xps \*檔案之後, 方法會將每個這類檔案新增至列印佇列。 此範例假設印表機不是 XPSDrv, 所以我們會傳遞`false`至<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>方法的最後一個參數。 基於這個理由, 方法會先驗證檔案中的 XPS 標記, 再嘗試將它轉換成印表機的分頁描述語言。 如果驗證失敗，則會擲回例外狀況。 範例程式碼會攔截例外狀況、通知使用者, 然後繼續處理下一個 XPS 檔案。  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 如果您使用 XPSDrv 印表機，則可以將最終參數設定為 `true`。 在這種情況下, 由於 XPS 是印表機的分頁描述語言, 因此方法會將檔案傳送到印表機, 而不會進行驗證, 或將它轉換成其他分頁描述語言。 如果您在設計階段不確定應用程式是否會使用 XPSDrv 印表機, 您可以修改應用程式, 讓它根據找到的<xref:System.Printing.PrintQueue.IsXpsDevice%2A>內容來讀取屬性和分支。  
  
 由於在發行[!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]和 Microsoft .NET Framework 之後, 一開始會有少數的 XPSDrv 印表機可供使用, 因此您可能需要將非 xpsdrv 印表機偽裝成 xpsdrv 印表機。 若要這樣做，請將 Pipelineconfig.xml 新增至執行您應用程式之電腦的下列登錄機碼中的檔案清單︰  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\ *\<PseudoXPSPrinter>* \DependentFiles  
  
 其中 *\<PseudoXPSPrinter>* 是任何列印佇列。 電腦之後必須重新開機。  
  
 這種偽裝方式可讓您`true`傳遞做為的最後<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>一個參數, 而不會造成例外狀況, 但由於 *\<pseudoxpsprinter> >* 並不是 XPSDrv 印表機, 因此只會列印垃圾。  
  
 **注意**為了簡單起見, 上述範例會使用 .xps 副檔名, \*做為其測試檔案為 xps。 不過, XPS 檔案不一定要有此延伸模組。 [IsXPS (IsXPS 一致性工具)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100))是測試檔案以取得 XPS 有效性的一種方式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.AddJob%2A>
- <xref:System.Threading.ApartmentState>
- <xref:System.STAThreadAttribute>
- [XPS 檔](/windows/desktop/printdocs/documents)
- [列印 XPS 檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90))
- [Managed 和非受控執行緒](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [isXPS.exe (isXPS 一致性工具)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100))
- [WPF 中的文件](documents-in-wpf.md)
- [列印概觀](printing-overview.md)
