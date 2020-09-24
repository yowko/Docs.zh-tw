---
title: 取得範例 SQL Server 資料庫以 ADO.NET 程式碼範例
description: 下載 ADO.NET 檔中的程式碼範例所使用的範例 SQL Server 資料庫，以及 SQL Server 和管理工具
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: f7c0d1eb0089a6bfabc92e1deecf563c3e59cc6a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156052"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>取得 ADO.NET 程式碼範例的範例資料庫

檔中的一些範例和逐步解說會 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 使用範例 SQL Server 資料庫和 SQL Server Express。 您可以從 Microsoft 免費下載這些產品。

## <a name="get-the-northwind-sample-database-for-sql-server"></a>取得 SQL Server 的 Northwind 範例資料庫

`instnwnd.sql`從下列 GitHub 存放庫下載腳本，以建立和載入 SQL Server 的 Northwind 範例資料庫：

[Microsoft SQL Server 的 Northwind 和 pubs 範例資料庫](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

使用 Northwind 資料庫之前，您必須執行下載的腳本檔案， `instnwnd.sql` 以使用 [SQL Server Management Studio](#get_ssms) 或類似的工具，在 SQL Server 的實例上重新建立資料庫。 遵循存放庫中讀我檔案中的指示。

> [!TIP]
> 如果您要尋找適用于 Microsoft Access 的 Northwind 資料庫，請參閱 [安裝適用于 Microsoft access 的 northwind 範例資料庫](#northwind_access)。

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a> 取得 Microsoft Access 的 Northwind 範例資料庫

Microsoft 下載中心不提供適用于 Microsoft Access 的 Northwind 範例資料庫。 若要直接從 Access 內安裝 Northwind，請執行下列動作：

1. 開啟存取權。

1. 在 [**搜尋線上範本**] 方塊中輸入**Northwind** ，然後選取**enter**。

1. 在 [結果] 畫面上，選取 [ **Northwind**]。 新視窗隨即開啟，其中包含 Northwind 資料庫的描述。

1. 在新視窗的 [ **檔案名** ] 文字方塊中，提供您的 Northwind 資料庫複本的檔案名。

1. 選取 [建立]。 存取會下載 Northwind 資料庫，並準備檔案。

1. 當此程式完成時，資料庫會以歡迎畫面開啟。

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>取得 SQL Server 的 AdventureWorks 範例資料庫

從下列 GitHub 存放庫下載 SQL Server 的 AdventureWorks 範例資料庫：

[AdventureWorks 範例資料庫](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

下載其中一個資料庫備份 (\* .bak) 檔案之後，請使用 SQL Server Management Studio (SSMS) ，將備份還原至 SQL Server 的實例。 請參閱 [Get SQL Server Management Studio](#get_ssms)。

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a> 取得 SQL Server Management Studio

如果您想要查看或修改已下載的資料庫，您可以使用 SQL Server Management Studio (SSMS) 。 從下列頁面下載 SSMS：

[下載 SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms)

您也可以在 Visual Studio 整合式開發環境中， (IDE) 來查看及管理資料庫。 在 [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)中，從 **SQL Server 物件總管**連接到資料庫，或在 **伺服器總管**中建立資料庫的資料連線。 從 [ **View** ] 功能表開啟這些 [explorer] 窗格。

## <a name="get-sql-server-express"></a><a name="get_sql"></a> 取得 SQL Server Express

SQL Server Express 是免費的入門版 SQL Server，可讓您隨應用程式一起轉散發。 從下列頁面下載 SQL Server Express：
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

如果您使用 [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)，SQL Server Express LocalDB 會包含在 Visual Studio 的免費版和更高版本中。  

## <a name="see-also"></a>另請參閱

- [快速入門](getting-started.md)
