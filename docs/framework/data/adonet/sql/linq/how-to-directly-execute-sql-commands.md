---
title: 如何：直接執行 SQL 命令
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 90fb0d7027946ce4f38c2ba4930ac3510e2a42b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351868"
---
# <a name="how-to-directly-execute-sql-commands"></a>如何：直接執行 SQL 命令
在假設使用 <xref:System.Data.Linq.DataContext> 集合的情況下，您可以使用 <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> 執行不會傳回物件的 SQL 命令。  
  
## <a name="example"></a>範例  
 下列範例會讓 SQL Server 將 UnitPrice 增加 1.00。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>另請參閱  
 [如何：直接執行 SQL 查詢](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)  
 [與資料庫通訊](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
