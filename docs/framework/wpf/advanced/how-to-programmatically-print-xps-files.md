---
title: "如何：以程式設計方式列印 XPS 檔 | Microsoft Docs"
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
  - "以程式設計方式列印 XPS 檔"
  - "XPS 檔案, 以程式設計方式列印"
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：以程式設計方式列印 XPS 檔
您可以使用 <xref:System.Printing.PrintQueue.AddJob%2A> 方法的其中一個多載來列印 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] 檔案，而不需要開啟 <xref:System.Windows.Controls.PrintDialog>，原則上根本也不需要開啟任何[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。  
  
 也可以使用 <xref:System.Windows.Xps.XpsDocumentWriter> 的許多 <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> 和 <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> 方法，來列印 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] 檔案。  如需此方面的詳細資訊，請參閱[Printing an XPS Document](http://msdn.microsoft.com/zh-tw/849555c8-0c4e-48c0-86bc-a5494c69b36c)。  
  
 另一種列印 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] 的方式是使用 <xref:System.Windows.Controls.PrintDialog> 控制項的 <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> 或 <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> 方法。  請參閱 [叫用列印對話方塊](../../../../docs/framework/wpf/advanced/how-to-invoke-a-print-dialog.md)。  
  
## 範例  
 使用由三個參數組成之 <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> 方法的主要步驟如下。  下面範例會提供詳細資料。  
  
1.  判斷印表機是否為 XPSDrv 印表機   \(如需 XPSDrv 的詳細資訊，請參閱[列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)\)。  
  
2.  如果印表機不是 XPSDrv 印表機，請將執行緒的 Apartment 設為單一執行緒。  
  
3.  具現化 \(Instantiate\) 列印伺服器和列印佇列物件。  
  
4.  呼叫方法，用以指定工作名稱、要列印的檔案，以及表示印表機是否為 XPSDrv 印表機的 <xref:System.Boolean> 旗標。  
  
 下面的範例顯示如何將目錄中的所有 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 檔案進行批次列印。  雖然應用程式會提示使用者指定目錄，但是由三個參數組成的 <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> 方法並不需要[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。  它可以用於任何具有 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 檔案名稱的程式碼路徑，以及可以\\存取的路徑。  
  
 當 <xref:System.Boolean> 參數是 `false` 時 \(使用非 XPSDrv 印表機時必須為此值\)，<xref:System.Printing.PrintQueue.AddJob%2A> 之由三個參數組成的 <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> 多載就必須在單一執行緒 Apartment 中執行。  然而，[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] 的預設 Apartment 狀態是多執行緒。  因為範例假設的是非 XPSDrv 印表機，所以必須改變這個預設值。  
  
 變更預設值的方式有兩種。  其中一種方式只要將 <xref:System.STAThreadAttribute> \(即 "`[System.STAThreadAttribute()]`"\) 加入至應用程式之 `Main` 方法的第一行上方 \(通常是 "`static void Main(string[] args)`"\)。  然而，許多應用程式還需要 `Main` 方法具有多執行緒 Apartment 狀態，因此另有第二種方法：在不同執行緒中進行 <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> 的呼叫，這個執行緒的 Apartment 狀態是使用 <xref:System.Threading.Thread.SetApartmentState%2A> 設為 <xref:System.Threading.ApartmentState>。  下面範例使用的是第二種技術。  
  
 因此，範例一開始是具現化 <xref:System.Threading.Thread> 物件，並將 **PrintXPS** 方法傳遞給它做為 <xref:System.Threading.ThreadStart> 參數   \(**PrintXPS** 方法稍後將於範例中定義\)。 接下來，將執行緒設為單一執行緒 Apartment。  而 `Main` 方法中唯一餘下的程式碼會啟動新的執行緒。  
  
 範例的主要部分是 `static` **BatchXPSPrinter.PrintXPS** 方法。  建立列印伺服器和佇列之後，方法會提示使用者輸入含有 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 檔案的目錄。  而在驗證目錄及其內的 \*.xps 檔案確實存在之後，方法會將每個這類檔案加入至列印佇列。  範例假設印表機是非 XPSDrv，所以會將 `false` 傳遞給 <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> 方法的最後一個參數。  因此，方法會先驗證檔案中的 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 標記，再嘗試將它轉換為印表機的頁面描述語言。  如果驗證失敗，則會擲回例外狀況。  而範例程式碼會攔截例外狀況、通知使用者發生例外狀況，然後繼續處理下一個 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 檔案。  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 如果使用的是 XPSDrv 印表機，則可以將最終參數設為 `true`。  在該情況下，因為 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 是印表機的頁面描述語言，所以方法會將檔案傳送給印表機，而不需要進行驗證，或將它轉換為另一種頁面描述語言。  如果在設計階段不確定應用程式是否使用 XPSDrv 印表機，則可以修改應用程式，讓它根據找到的內容讀取 <xref:System.Printing.PrintQueue.IsXpsDevice%2A> 屬性作判斷。  
  
 因為一開始在發行 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] 和 [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] 之後立即可用的 XPSDrv 印表機很少，所以可能需要將非 XPSDrv 印表機偽裝成 XPSDrv 印表機。  若要執行此作業，請在執行應用程式之電腦的下列登錄機碼 \(Registry Key\) 中，將 Pipelineconfig.xml 加入至檔案清單：  
  
 HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Print\\Environments\\Windows NT x86\\Drivers\\Version\-3\\*\<PseudoXPSPrinter\>*\\DependentFiles  
  
 其中，*\<PseudoXPSPrinter\>* 是任意列印佇列。  然後必須將電腦重新開機。  
  
 這項偽裝可讓您傳遞 `true` 做為 <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> 的最終參數，而不會造成例外狀況，但是因為 *\<PseudoXPSPrinter\>* 不是真正的 XPSDrv 印表機，所以只會印出亂碼。  
  
 **注意**：為了簡化，上面的範例使用 \*.xps 副檔名的存在與否來測試檔案是否為 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]。  然而，[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 檔案並不一定是這個副檔名。  [isXPS.exe \(isXPS 一致性工具\)](../Topic/isXPS.exe%20\(isXPS%20Conformance%20Tool\).md)是測試檔案是否具有 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 有效性的一種方式。  
  
## 請參閱  
 <xref:System.Printing.PrintQueue>   
 <xref:System.Printing.PrintQueue.AddJob%2A>   
 <xref:System.Threading.ApartmentState>   
 <xref:System.STAThreadAttribute>   
 [XPS](http://www.microsoft.com/xps)   
 [Printing an XPS Document](http://msdn.microsoft.com/zh-tw/849555c8-0c4e-48c0-86bc-a5494c69b36c)   
 [Managed and Unmanaged Threading](http://msdn.microsoft.com/zh-tw/db425c20-4b2f-4433-bf96-76071c7881e5)   
 [isXPS.exe \(isXPS 一致性工具\)](../Topic/isXPS.exe%20\(isXPS%20Conformance%20Tool\).md)   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)