---
title: 多項大量複製作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 838f56311f165c99c71cc734576bbdb53a946b7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792074"
---
# <a name="multiple-bulk-copy-operations"></a>多項大量複製作業
您可以使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別的單一執行個體，執行多項大量複製作業。 如果作業參數在複本之間有所變更（例如目的地資料表的名稱），您必須在任何後續呼叫任何**WriteToServer**方法之前更新它們，如下列範例所示。 除非明確地變更，否則所有屬性值都會保持與給定執行個體之前次大量複製作業時的值相同。  
  
> [!NOTE]
> 執行多項大量複製作業時，使用同一個 <xref:System.Data.SqlClient.SqlBulkCopy> 執行個體通常會比每個作業使用不同的執行個體更有效率。  
  
 使用相同的 <xref:System.Data.SqlClient.SqlBulkCopy> 物件執行數個大量複製作業時，對每個作業中的來源或目標資訊是否相等或不同並沒有限制。 但是，您必須確保每次寫入伺服器時，資料行關聯資訊的設定都正確。  
  
> [!IMPORTANT]
> 除非您已如[大量複製範例設定](bulk-copy-example-setup.md)中所述建立工作資料表，否則此範例不會執行。 這段程式碼是為了示範只使用**SqlBulkCopy**的語法而提供。 如果來源及目的地資料表位於相同的 SQL Server 執行個體中，則使用 Transact-SQL `INSERT … SELECT` 陳述式來複製資料會更方便且快速。  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [在 SQL Server 中執行大量複製作業](bulk-copy-operations-in-sql-server.md)
- [ADO.NET 概觀](../ado-net-overview.md)
