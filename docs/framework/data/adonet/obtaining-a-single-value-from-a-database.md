---
title: 從資料庫取得單一值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: 5eb81fd2a64f06f1252f71e251e58df568e7407c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120675"
---
# <a name="obtaining-a-single-value-from-a-database"></a>從資料庫取得單一值
或許您需要以單一數值傳回資料庫資訊，而非以資料表或資料流的形式。 比方說，您可能想要傳回的結果，例如計數彙總函式 (\*)，sum （price） 或 AVG(Quantity)。 **命令**物件可讓您使用的單一值傳回到**ExecuteScalar**方法。 **ExecuteScalar**方法傳回時，為純量值時，結果集的第一個資料列的第一個資料行的值。  
  
 下列程式碼範例會使用 <xref:System.Data.SqlClient.SqlCommand>，在資料庫中插入新的值。 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> 方法是用來傳回所插入資料錄的識別資料行值。  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [執行命令](../../../../docs/framework/data/adonet/executing-a-command.md)
- [DbConnection、DbCommand 和 DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
