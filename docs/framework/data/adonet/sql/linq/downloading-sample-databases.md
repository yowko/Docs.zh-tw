---
title: 取得 ADO.NET 程式碼範例的範例 SQL Server 資料庫
description: 下載 ADO.NET 檔中程式碼範例所使用的範例 SQL Server 資料庫，以及 SQL Server 和管理工具
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 60566041ff4f99e96c9aee052dbcc17b5e5da9e5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794037"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>取得 ADO.NET 程式碼範例的範例資料庫

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]檔中的一些範例和逐步解說會使用範例 SQL Server 資料庫和 SQL Server Express。 您可以從 Microsoft 免費下載這些產品。

## <a name="get-the-northwind-sample-database-for-sql-server"></a>取得適用于 SQL Server 的 Northwind 範例資料庫

從下列 GitHub `instnwnd.sql`存放庫下載腳本，以建立和載入 SQL Server 的 Northwind 範例資料庫：

[適用于 Microsoft SQL Server 的 Northwind 和 pubs 範例資料庫](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

在您可以使用 Northwind 資料庫之前，您必須先執行下載`instnwnd.sql`的腳本檔案，使用[SQL Server Management Studio](#get_ssms)或類似的工具，在 SQL Server 的實例上重新建立資料庫。 遵循存放庫中的讀我檔案中的指示。

> [!TIP]
> 如果您要尋找適用于 Microsoft Access 的 Northwind 資料庫，請參閱[安裝適用于 Microsoft access 的 northwind 範例資料庫](#northwind_access)。

## <a name="northwind_access"></a>取得適用于 Microsoft Access 的 Northwind 範例資料庫

Microsoft 下載中心不提供適用于 Microsoft Access 的 Northwind 範例資料庫。 若要直接從存取中安裝 Northwind，請執行下列動作：

1. 開啟 [存取]。

1. 在 [**搜尋線上範本**] 方塊中輸入**Northwind** ，然後選取**Enter**。

1. 在 [結果] 畫面上，選取 [ **Northwind**]。 新視窗隨即開啟，其中含有 Northwind 資料庫的描述。

1. 在新視窗的 [**檔案名**] 文字方塊中，為您的 Northwind 資料庫複本提供檔案名。

1. 選取 [建立]。 Access 會下載 Northwind 資料庫，並準備檔案。

1. 當此程式完成時，資料庫就會開啟並顯示 [歡迎使用] 畫面。

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>取得適用于 SQL Server 的 AdventureWorks 範例資料庫

從下列 GitHub 存放庫下載適用于 SQL Server 的 AdventureWorks 範例資料庫：

[AdventureWorks 範例資料庫](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

在您下載其中一個資料庫備份（\*.bak）檔案之後，請使用 SQL Server Management Studio （SSMS）將備份還原到 SQL Server 的實例。 請參閱[取得 SQL Server Management Studio](#get_ssms)。

## <a name="get_ssms"></a>取得 SQL Server Management Studio
如果您想要查看或修改已下載的資料庫，您可以使用 SQL Server Management Studio （SSMS）。 從下列頁面下載 SSMS：

[下載 SQL Server Management Studio （SSMS）](/sql/ssms/download-sql-server-management-studio-ssms) 

您也可以在 Visual Studio 整合式開發環境（IDE）中查看和管理資料庫。 在[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)中，從**SQL Server 物件總管**連接到資料庫，或在**伺服器總管**中建立資料庫的資料連線。 從 [ **View** ] 功能表開啟這些 [瀏覽器] 窗格。

## <a name="get_sql"></a>取得 SQL Server Express

SQL Server Express 是免費的入門版的 SQL Server，可讓您隨著應用程式轉散發。 從下列頁面下載 SQL Server Express：
  
[SQL Server Express 版本](https://www.microsoft.com/sql-server/sql-server-editions-express)

如果您使用的是[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)，SQL Server Express LocalDB 會包含在免費的 Visual Studio 的社區版本中，以及 Professional 和更高版本中。  

## <a name="see-also"></a>另請參閱

- [快速入門](getting-started.md)
