---
title: 取得範例 SQL Server 資料庫的 ADO.NET 程式碼範例
description: 下載 ADO.NET 文件，以及 SQL Server 和管理工具的程式碼範例中所使用的 SQL Server 範例資料庫
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 5580f06f3d28ed6d70f75b619498ac8de7bc3326
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307288"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>取得範例資料庫的 ADO.NET 程式碼範例

許多範例和逐步解說中的[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]文件使用的 SQL Server 範例資料庫和 SQL Server Express。 您可以從 Microsoft 下載這些免費的產品。

## <a name="get-the-northwind-sample-database-for-sql-server"></a>取得 SQL Server 的 Northwind 範例資料庫

下載指令碼`instnwnd.sql`從下列的 GitHub 存放庫，來建立和載入適用於 SQL Server 的 Northwind 範例資料庫：

[Microsoft SQL server 的 Northwind 和 pubs 範例資料庫](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

您可以使用 Northwind 資料庫之前，您必須執行已下載`instnwnd.sql`重新建立 SQL Server 執行個體上的資料庫所使用的指令碼檔案[SQL Server Management Studio](#get_ssms)或類似的工具。 請遵循存放庫中的讀我檔案中的指示。

> [!TIP]
> 如果您想為 Microsoft Access Northwind 資料庫，請參閱[安裝 Microsoft Access Northwind 範例資料庫](#northwind_access)。

## <a name="northwind_access"></a> 取得 Microsoft Access Northwind 範例資料庫

Microsoft Download Center 上，不可以使用 Microsoft access Northwind 範例資料庫。 若要安裝在 Access 中的直接從 Northwind，執行下列動作：

1. 開啟 [存取]。

1. Enter **Northwind**中**搜尋線上範本**方塊，然後按**Enter**。

1. 在 [結果] 畫面中，選取**Northwind**。 新的視窗會開啟 Northwind 資料庫的描述。

1. 在新視窗中，在**檔案名**文字中，提供檔案名稱，為您的 Northwind 資料庫的副本。

1. 選取 [建立]。 存取下載 Northwind 資料庫，並準備此檔案。

1. 完成此程序時，資料庫便會開啟 歡迎使用畫面。

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>取得 SQL Server 的 AdventureWorks 範例資料庫

適用於 SQL Server，從下列 GitHub 儲存機制下載 AdventureWorks 範例資料庫：

[AdventureWorks 範例資料庫](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

下載其中一個資料庫備份之後 (\*.bak) 檔案，使用 SQL Server Management Studio (SSMS) 將備份還原到 SQL Server 的執行個體。 請參閱[取得 SQL Server Management Studio](#get_ssms)。

## <a name="get_ssms"></a> 取得 SQL Server Management Studio
如果您想要檢視或修改的資料庫，您已下載，您可以使用 SQL Server Management Studio (SSMS)。 下載 SSMS，從下列頁面：

[下載 SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) 

您也可以檢視和管理 Visual Studio 整合式的開發環境 (IDE) 中的資料庫。 在[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)，連接到資料庫**SQL Server 物件總管**，或建立的資料庫中的資料連接**伺服器總管**。 開啟這些檔案總管 窗格，從**檢視**功能表。

## <a name="get_sql"></a> Get SQL Server Express

SQL Server Express 是免費的入門級的 SQL Server 版本，您可以重新發佈的應用程式。 下載 SQL Server Express 從下列頁面：
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

如果您使用[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)，SQL Server Express LocalDB 納入的 Visual Studio 中，免費的 Community edition，以及專業和更高版本。  

## <a name="see-also"></a>另請參閱

- [快速入門](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
