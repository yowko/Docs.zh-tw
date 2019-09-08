---
title: 在 SQL Server 中執行大量複製作業
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: ae97bcdd6776d573cf9e523133c2c00a42c273bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782520"
---
# <a name="bulk-copy-operations-in-sql-server"></a>在 SQL Server 中執行大量複製作業
Microsoft SQL Server 包含名為**bcp**的熱門命令列公用程式，可快速地將大型檔案大量複製到 SQL Server 資料庫中的資料表或 views。 <xref:System.Data.SqlClient.SqlBulkCopy> 類別可讓您撰寫會提供類似功能的 Managed 程式碼方案。 還可採用其他方式將資料載入 SQL Server 資料表 (例如，INSERT 陳述式)，但 <xref:System.Data.SqlClient.SqlBulkCopy> 的效能優勢明顯高於它們。  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> 類別可用於僅將資料寫入 SQL Server 資料表。 但是資料來源不僅限於 SQL Server；可使用任何資料來源，只要該資料可載入 <xref:System.Data.DataTable> 執行個體，或可使用 <xref:System.Data.IDataReader> 執行個體進行讀取。  
  
 使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別，您可以執行：  
  
- 單一大量複製作業  
  
- 多項大量複製作業  
  
- 在交易內的大量複製作業  
  
> [!NOTE]
> 使用 .NET Framework 1.1 版或更早版本（不支援<xref:System.Data.SqlClient.SqlBulkCopy>類別）時，您可以使用<xref:System.Data.SqlClient.SqlCommand>物件來執行 SQL Server transact-sql **BULK INSERT**語句。  
  
## <a name="in-this-section"></a>本節內容  
 [大量複製範例設定](bulk-copy-example-setup.md)  
 說明大量複製範例中使用的資料表，並提供用於在 AdventureWorks 資料庫中建立資料表的 SQL 指令碼。  
  
 [單一大量複製作業](single-bulk-copy-operations.md)  
 說明如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別將資料單一大量複製到 SQL Server 的執行個體中，以及如何使用 Transact-SQL 陳述式及 <xref:System.Data.SqlClient.SqlCommand> 類別執行大量複製作業。  
  
 [多項大量複製作業](multiple-bulk-copy-operations.md)  
 說明如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別，執行資料到 SQL Server 執行個體的多項大量複製作業。  
  
 [異動和大量複製作業](transaction-and-bulk-copy-operations.md)  
 說明如何在異動內執行大量複製作業，包含如何認可或復原異動。  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 和 ADO.NET](index.md)
- [ADO.NET 概觀](../ado-net-overview.md)
