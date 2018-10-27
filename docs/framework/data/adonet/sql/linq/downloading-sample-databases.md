---
title: 取得範例資料庫的 ADO.NET 程式碼範例
description: 下載範例資料庫中的 ADO.NET 文件，以及 SQL Server 和管理工具的程式碼範例使用
ms.date: 10/18/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 9779300288135cb9332a028d547ce55a07e89471
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188387"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>取得範例資料庫的 ADO.NET 程式碼範例

許多範例和逐步解說中的[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]文件使用範例資料庫和 SQL Server Express。 您可以從 Microsoft 下載這些免費的產品。

## <a name="get-the-northwind-sample-database"></a>取得 Northwind 範例資料庫

從 Microsoft 下載中心中的下列頁面下載 Northwind 範例資料庫：

[Northwind 和 Pubs 範例資料庫](https://go.microsoft.com/fwlink?linkid=64296)

下載檔案之後，連按兩下該檔案以解壓縮資料庫與指令碼。 根據預設，檔案會安裝在資料夾`<drive>:\SQL Server 2000 Sample Databases`。

您可以使用 Northwind 資料庫之前，您必須使用 重新建立資料庫的 SQL Server 執行個體上[SQL Server Management Studio](#get_ssms)或類似工具來執行`instnwnd.sql`安裝資料夾中的指令碼檔案。

## <a name="get-the-adventureworks-sample-database"></a>取得 AdventureWorks 範例資料庫

從下列 GitHub 儲存機制下載 AdventureWorks 範例資料庫：

[AdventureWorks 範例資料庫](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

下載其中一個資料庫備份之後 (\*.bak) 檔案，使用 SQL Server Management Studio (SSMS) 將備份還原到 SQL Server 的執行個體。 請參閱[取得 SQL Server Management Studio](#get_ssms)。

## <a name="get_sql"></a> 取得 SQL Server Express

SQL Server Express 是免費的入門級的 SQL Server 版本，您可以重新發佈的應用程式。 下載 SQL Server Express 從下列頁面：
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

如果您使用[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)，SQL Server Express LocalDB 納入免費的 Community edition，以及專業和更高版本。  

## <a name="get_ssms"></a> 取得 SQL Server Management Studio
如果您想要檢視或修改的資料庫，您已下載，您可以使用 SQL Server Management Studio (SSMS)。 下載 SSMS，從下列頁面：

[下載 SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) 

您也可以檢視和管理 Visual Studio 整合式的開發環境 (IDE) 中的資料庫。 在[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)，連接到資料庫**SQL Server 物件總管**，或建立的資料庫中的資料連接**伺服器總管**。 開啟這些檔案總管 窗格，從**檢視**功能表。
  
## <a name="see-also"></a>另請參閱

- [快速入門](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
