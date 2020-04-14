---
title: SQL 追蹤
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 72bfcaac2903b3e7fa5679422ad4feaa79e93211
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243176"
---
# <a name="sql-tracking"></a>SQL 追蹤

此示例演示如何編寫將跟蹤記錄寫入 SQL 資料庫的自定義 SQL 跟蹤參與者。 Windows 工作流基礎 (WF) 提供工作流跟蹤,以深入瞭解工作流實例的執行。 追蹤執行階段會在工作流程執行期間發出工作流程追蹤記錄。 有關工作流追蹤的詳細資訊,請參閱[工作流追蹤並追蹤](../workflow-tracking-and-tracing.md)。

## <a name="use-the-sample"></a>使用範例

1. 確定您已安裝 SQL Server 2008、SQL Server 2008 Express 或更新版本。 隨範例封裝的指令碼假定在本機電腦上使用 SQL Express 執行個體。 如果您有不同的執行個體，在執行範例之前請先修改資料庫相關指令碼。

2. 執行指令碼目錄 (\WF\Basic\Tracking\SqlTracking\CS\Scripts) 中的 Trackingsetup.cmd，建立 SQL Server 追蹤資料庫。 這會建立名為 TrackingSample 的資料庫。

   > [!NOTE]
   > 指令碼會在 SQL Express 預設執行個體上建立資料庫。 如果您想要安裝在不同的資料庫執行個體上，請編輯 Trackingsetup.cmd 指令碼。

3. 在視覺工作室 2010 中打開 SqlTrackingSample.sln。

4. 按**Ctrl**+**移位**+**B**可建構解決方案。

5. 按**F5**以運行應用程式。

   瀏覽器視窗隨即開啟並顯示應用程式的目錄清單。

6. 在瀏覽器中，按一下 StockPriceService.xamlx。

7. 瀏覽器隨即顯示 StockPriceService 頁面，其中包含本機服務 WSDL 位址。 複製此位址。

   本地服務 WSDL 位址的`http://localhost:65193/StockPriceService.xamlx?wsdl`範例是 。

8. 使用檔案資源管理員運行 WCF 測試用戶端 (WcfTestClient.exe)。 它位於*微軟視覺工作室 10.0_Common7_IDE 目錄中*。

9. 在 WCF 測試用戶端中,按下 **「檔**」功能表並選擇「**新增服務**」。 將本機服務位址貼至文字方塊。 按一下 **[確定]** 關閉對話方塊。

10. 在 WCF 測試客戶端中,按兩下**GetStockPrice**。 這將打開需要`GetStockPrice`一個參數的操作,鍵入值`Contoso`並按下 **「調用**」。

11. 發出的追蹤記錄會寫入至 SQL 資料庫。 若要檢視追蹤記錄，請在 SQL Management Studio 中開啟 TrackingSample 資料庫並巡覽至資料表。 在資料表上執行 Select 查詢，會顯示個別資料表中所儲存的追蹤記錄資料。

   有關 SQL 伺服器管理工作室的詳細資訊,請參閱[介紹 SQL 伺服器管理工作室](/sql/ssms/sql-server-management-studio-ssms)。 [在此處](https://aka.ms/ssmsfullsetup)下載 SQL 伺服器管理工作室。

## <a name="uninstall-the-sample"></a>卸載範例

1. 在範例目錄中運行追蹤清理.cmd 文稿 *(\WF_基本\跟蹤\Sql 跟蹤*)。

    > [!NOTE]
    > Trackingcleanup.cmd 會嘗試刪除本機電腦 SQL Express 中的資料庫。 如果您使用另一個 SQL Server 執行個體，請編輯 Trackingcleanup.cmd。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在,請轉到[Windows 通信基礎 (WCF) 和 Windows 工作流基礎 (WF) 範例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通訊基礎 (WCF) 和示例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a>另請參閱

- [AppFabric 監控範例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
