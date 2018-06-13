---
title: SQL 追蹤
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 9c42690570fb3f90f576327dcc5cfe870288b99a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518299"
---
# <a name="sql-tracking"></a>SQL 追蹤
此範例示範如何撰寫自訂的 SQL 追蹤參與者，將追蹤記錄寫入至 SQL 資料庫。 Windows Workflow Foundation (WF) 提供工作流程追蹤，讓您查看工作流程執行個體執行。 追蹤執行階段會在工作流程執行期間發出工作流程追蹤記錄。 如需工作流程追蹤的詳細資訊，請參閱[工作流程追蹤](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  確定您已安裝 SQL Server 2008、SQL Server 2008 Express 或更新版本。 隨範例封裝的指令碼假定在本機電腦上使用 SQL Express 執行個體。 如果您有不同的執行個體，在執行範例之前請先修改資料庫相關指令碼。  
  
2.  執行指令碼目錄 (\WF\Basic\Tracking\SqlTracking\CS\Scripts) 中的 Trackingsetup.cmd，建立 SQL Server 追蹤資料庫。 這會建立名為 TrackingSample 的資料庫。  
  
    > [!NOTE]
    >  指令碼會在 SQL Express 預設執行個體上建立資料庫。 如果您想要安裝在不同的資料庫執行個體上，請編輯 Trackingsetup.cmd 指令碼。  
  
3.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 SqlTrackingSample.sln。  
  
4.  按下 CTRL+SHIFT+B 以建置方案。  
  
5.  按 F5 執行應用程式。  
  
     瀏覽器視窗隨即開啟並顯示應用程式的目錄清單。  
  
6.  在瀏覽器中，按一下 StockPriceService.xamlx。  
  
7.  瀏覽器隨即顯示 StockPriceService 頁面，其中包含本機服務 WSDL 位址。 複製此位址。  
  
     本機服務 WSDL 位址的範例是http://localhost:65193/StockPriceService.xamlx?wsdl。  
  
8.  使用 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] 來執行 WCF 測試用戶端 (WcfTestClient.exe)。 它是位於 Microsoft Visual Studio 10.0\Common7\IDE 目錄中。  
  
9. 在 WCF 測試用戶端中，按一下 **檔案**功能表，然後選取**加入服務**。 將本機服務位址貼至文字方塊。 按一下**確定**以關閉對話方塊。  
  
10. 在 WCF 測試用戶端中，按兩下  **GetStockPrice**。 這會開啟`GetStockPrice`接受一個參數，輸入的值的作業`Contoso`按一下**Invoke**。  
  
11. 發出的追蹤記錄會寫入至 SQL 資料庫。 若要檢視追蹤記錄，請在 SQL Management Studio 中開啟 TrackingSample 資料庫並巡覽至資料表。 如需有關 SQL Server Management Studio 的詳細資訊，請參閱[SQL Server Management Studio 簡介](http://go.microsoft.com/fwlink/?LinkId=165645)。 您可以下載 SQL Server 2008 Management Studio Express[這裡](http://go.microsoft.com/fwlink/?LinkId=180520)。 在資料表上執行 Select 查詢，會顯示個別資料表中所儲存的追蹤記錄資料。  
  
#### <a name="to-uninstall-the-sample"></a>若要解除安裝範例  
  
1.  執行範例目錄 (\WF\Basic\Tracking\SqlTracking) 中的 theTrackingcleanup.cmd 指令碼。  
  
    > [!NOTE]
    >  Trackingcleanup.cmd 會嘗試刪除本機電腦 SQL Express 中的資料庫。 如果您使用另一個 SQL Server 執行個體，請編輯 Trackingcleanup.cmd。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 監控範例](http://go.microsoft.com/fwlink/?LinkId=193959)
