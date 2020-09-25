---
title: 在 SQL Server 中執行大量複製作業
description: 瞭解如何使用 SqlBulkCopy 類別撰寫 managed 程式碼解決方案，以大量將大型檔案複製到 SQL Server 資料庫中的資料表或觀點。
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 43d63f3671ea8ff05da3e10580c2784fa3aae581
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197426"
---
# <a name="bulk-copy-operations-in-sql-server"></a>在 SQL Server 中執行大量複製作業

Microsoft SQL Server 包含名為 **bcp** 的常用命令列公用程式，用於將大型檔案快速大量複製到 SQL Server 資料庫中的資料表或檢視。 <xref:System.Data.SqlClient.SqlBulkCopy> 類別可讓您撰寫受控程式碼解決方案來提供類似功能。 還有其他方法可以將資料載入 SQL Server 資料表 (例如 INSERT 陳述式)，但 <xref:System.Data.SqlClient.SqlBulkCopy> 提供顯著超越其他方法的效能優勢。  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> 類別只能用來將資料寫入到 SQL Server 資料表。 但是資料來源不僅限於 SQL Server；可使用任何資料來源，只要該資料可載入 <xref:System.Data.DataTable> 執行個體，或可使用 <xref:System.Data.IDataReader> 執行個體進行讀取。  
  
 使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別，您可以執行：  
  
- 單一大量複製作業  
  
- 多項大量複製作業  
  
- 交易內的大量複製作業  
  
> [!NOTE]
> 當使用 .NET Framework 1.1 版或更早版本 (不支援 <xref:System.Data.SqlClient.SqlBulkCopy> 類別) 時，您可使用 **物件執行 SQL Server Transact-SQL**BULK INSERT<xref:System.Data.SqlClient.SqlCommand> 陳述式。  
  
## <a name="in-this-section"></a>本節內容  

 [大量複製範例設定](bulk-copy-example-setup.md)  
 描述大量複製範例中所使用的資料表，並提供可用來在 AdventureWorks 資料庫中建立資料表的 SQL 指令碼。  
  
 [單一大量複製作業](single-bulk-copy-operations.md)  
 描述如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別，在 SQL Server 的執行個體中單一大量複製資料，以及如何使用 Transact-SQL 陳述式和 <xref:System.Data.SqlClient.SqlCommand> 類別來執行大量複製作業。  
  
 [多項大量複製作業](multiple-bulk-copy-operations.md)  
 描述如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別，在 SQL Server 的執行個體中執行資料的多個大量複製作業。  
  
 [交易和大量複製作業](transaction-and-bulk-copy-operations.md)  
 描述如何在交易內執行大量複製作業，包括如何認可或復原交易。  
  
## <a name="see-also"></a>另請參閱

- [SQL Server and ADO.NET](index.md) (SQL Server 和 ADO.NET)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
