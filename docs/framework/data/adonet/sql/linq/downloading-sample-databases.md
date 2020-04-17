---
title: 取得ADO.NET代碼範例的範例 SQL Server 資料庫
description: 下載ADO.NET文件中程式碼範例使用的範例 SQL Server 資料庫,以及 SQL Server 和管理工具
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 3449f502834f449f5023bd52457d45ffaf9b0fa1
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607980"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>取得ADO.NET代碼範例的範例資料庫

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]文檔中的一些範例和演練使用範例 SQL Server 資料庫和 SQL Server Express。 你可以從微軟免費下載這些產品。

## <a name="get-the-northwind-sample-database-for-sql-server"></a>取得 SQL Server 的北風範例資料庫

從以下`instnwnd.sql`GitHub 儲存函式庫下載文稿,以建立並載入 SQL Server 的北風範例資料庫:

[Northwind 和 pubs 範例資料庫為 Microsoft SQL 伺服器](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

在使用 Northwind 資料庫之前,必須執行`instnwnd.sql`下載的文稿檔,以便使用 SQL Server[管理工作室](#get_ssms)或類似工具在 SQL Server 實例上重新創建資料庫。 按照存儲庫中的 Readme 檔中的說明進行操作。

> [!TIP]
> 如果您要尋找適用於 Microsoft Access 的北風資料庫,請參閱[安裝 Microsoft Access 的北風範例資料庫](#northwind_access)。

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a>取得適用於 Microsoft 存取的北風範例資料庫

微軟訪問的北風示例資料庫在Microsoft下載中心不可用。 要直接從 Access 內部安裝北風,請執行以下操作:

1. 打開訪問。

1. 在 **「搜尋連線範本」** 框中輸入**北風**,然後選擇「**輸入**」。

1. 在結果螢幕上,選擇**北風**。 將打開一個新視窗,其中說明北風資料庫。

1. 在新視窗中,在 **「檔名**」文字框中,為北風資料庫的副本提供檔名。

1. 選取 [建立]  。 訪問下載北風資料庫並準備檔。

1. 此過程完成後,資料庫將打開,並帶有"歡迎"螢幕。

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>取得 SQL Server 的 AdventureWorks 範例資料庫

從以下 GitHub 儲存函式庫下載 SQL Server 的 AdventureWorks 範例資料庫:

[AdventureWorks 範例資料庫](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

下載其中一個資料庫備份 (.bak)\*檔案後,請使用 SQL Server 管理工作室 (SSMS) 將備份還原到 SQL Server 實例。 請參考[SQL 伺服器管理工作室](#get_ssms)。

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a>取得 SQL 伺服器管理工作室
如果要查看或修改已下載的資料庫,可以使用 SQL 伺服器管理工作室 (SSMS)。 從以下頁面下載 SSMS:

[下載 SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms)

您還可以在可視化工作室集成開發環境 (IDE) 中查看和管理資料庫。 在[可視化工作室](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)中,從 SQL**伺服器物件資源管理器**連接到資料庫,或在**伺服器資源管理器**中創建到資料庫的數據連接。 從 **「檢視」** 選單開啟這些資源管理器窗格。

## <a name="get-sql-server-express"></a><a name="get_sql"></a>取得 SQL 伺服器快速

SQL Server Express 是一個免費的入門級 SQL Server 版本,您可以使用應用程式重新分發。 從以下頁面下載 SQL 伺服器快速服務:
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

如果您使用的是[Visual Studio,SQL](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)Server Express 本地DB 包含在 Visual Studio 的免費社區版以及專業版和更高版本中。  

## <a name="see-also"></a>另請參閱

- [快速入門](getting-started.md)
