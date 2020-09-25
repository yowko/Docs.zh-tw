---
title: 作法：重複使用 ADO.NET 命令和 DataContext 之間的連接
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 89c9a12399d3d76487d1fdc2bd82aa037c167710
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197348"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>作法：重複使用 ADO.NET 命令和 DataContext 之間的連接

因為 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 是 ADO.NET 系列技術的一部分，而且是以 ADO.NET 提供的服務為基礎，所以您可以重複使用 ADO.NET 命令和之間的連接 <xref:System.Data.Linq.DataContext> 。  
  
## <a name="example"></a>範例  

 下列範例示範如何在 ADO.NET 命令和之間重複使用相同的連接 <xref:System.Data.Linq.DataContext> 。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>另請參閱

- [背景資訊](background-information.md)
- [ADO.NET 和 LINQ to SQL](ado-net-and-linq-to-sql.md)
- [與資料庫通訊](communicating-with-the-database.md)
