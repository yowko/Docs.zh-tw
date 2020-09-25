---
title: 多項大量複製作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: d447f09fcbfe108346b81a2bced44cf305e2844b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172667"
---
# <a name="multiple-bulk-copy-operations"></a>多項大量複製作業

您可以使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別的單一執行個體，執行多項大量複製作業。 如果作業參數在複本之間變更 (例如，目的地資料表的名稱) ，您必須在任何 **WriteToServer** 方法的後續呼叫之前更新這些參數，如下列範例所示。 除非已明確地變更，所有屬性值與之前指定執行個體上的大量複製作業維持相同。  
  
> [!NOTE]
> 比起對每項作業使用個別的執行個體，使用 <xref:System.Data.SqlClient.SqlBulkCopy> 的相同執行個體來執行多項大量複製作業通常更有效率。  
  
 如果您使用相同的 <xref:System.Data.SqlClient.SqlBulkCopy> 物件執行數項大量複製作業，並未限制來源或目標資訊在每項作業中是否相等或不同。 不過，當您每次寫入到伺服器時，必須確定資料行關聯資訊已正確設定。  
  
> [!IMPORTANT]
> 除非您已依照 [大量複製範例設定](bulk-copy-example-setup.md)所述建立工作資料表，否則此範例不會執行。 這個程式碼僅是為了示範使用 **SqlBulkCopy** 的語法而提供。 如果來源和目的地資料表位於相同的 SQL Server 執行個體，則使用 Transact-SQL `INSERT … SELECT` 陳述式來複製資料會更方便且快速。  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [在 SQL Server 中執行大量複製作業](bulk-copy-operations-in-sql-server.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
