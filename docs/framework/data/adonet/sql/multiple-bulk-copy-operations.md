---
title: 多項大量複製作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 267103e7315e337d223ce60652bdfddedbe4ec02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358130"
---
# <a name="multiple-bulk-copy-operations"></a>多項大量複製作業
您可以使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別的單一執行個體，執行多項大量複製作業。 如果複製 （例如，目的地資料表的名稱） 之間變更的作業參數，您必須先更新它們進行的任何後續呼叫**WriteToServer**方法，如下列範例所示。 除非明確地變更，否則所有屬性值都會保持與給定執行個體之前次大量複製作業時的值相同。  
  
> [!NOTE]
>  執行多項大量複製作業時，使用同一個 <xref:System.Data.SqlClient.SqlBulkCopy> 執行個體通常會比每個作業使用不同的執行個體更有效率。  
  
 使用相同的 <xref:System.Data.SqlClient.SqlBulkCopy> 物件執行數個大量複製作業時，對每個作業中的來源或目標資訊是否相等或不同並沒有限制。 但是，您必須確保每次寫入伺服器時，資料行關聯資訊的設定都正確。  
  
> [!IMPORTANT]
>  此範例不會執行，除非您已建立工作資料表中所述[大量複製範例設定](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)。 此程式碼可示範如何使用的語法**SqlBulkCopy**只。 如果來源及目的地資料表位於相同的 SQL Server 執行個體中，則使用 Transact-SQL `INSERT … SELECT` 陳述式來複製資料會更方便且快速。  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 [在 SQL Server 中執行大量複製作業](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
