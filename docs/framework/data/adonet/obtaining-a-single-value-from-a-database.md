---
title: 從資料庫取得單一值
description: 瞭解如何在 ADO.NET 中傳回單一值。 這個範例程式碼會傳回所插入記錄的識別資料行值。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: a6f268f72f8b8a09ae48ba3cad6254323cb95a20
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286698"
---
# <a name="obtaining-a-single-value-from-a-database"></a>從資料庫取得單一值
或許您需要以單一數值傳回資料庫資訊，而非以資料表或資料流的形式。 例如，您可能會想要傳回匯總函數的結果，例如 COUNT （ \* ）、SUM （Price）或 AVG （Quantity）。 **命令**物件提供使用**ExecuteScalar**方法傳回單一值的功能。 **ExecuteScalar**方法會以純量值傳回結果集中第一個資料列的第一個資料行的值。  
  
 下列程式碼範例會使用 <xref:System.Data.SqlClient.SqlCommand>，在資料庫中插入新的值。 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> 方法是用來傳回所插入資料錄的識別資料行值。  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [命令和參數](commands-and-parameters.md)
- [執行命令](executing-a-command.md)
- [DbConnection、DbCommand 和 DbException](dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
