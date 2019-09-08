---
title: 作法：重複使用 ADO.NET 命令和 DataContext 之間的連接
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: f1ee7726042327eae88e69e9e6d062909c5bc74e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793285"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>HOW TO：重複使用 ADO.NET 命令和 DataContext 之間的連接
由於[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]是 ADO.NET 系列技術的一部分，而且是以 ADO.NET 所提供的服務為基礎，因此，您可以重複使用 ADO.NET 命令<xref:System.Data.Linq.DataContext>與之間的連接。  
  
## <a name="example"></a>範例  
 下列範例示範如何在 ADO.NET 命令和<xref:System.Data.Linq.DataContext>之間重複使用相同的連接。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>另請參閱

- [背景資訊](background-information.md)
- [ADO.NET 和 LINQ to SQL](ado-net-and-linq-to-sql.md)
- [與資料庫通訊](communicating-with-the-database.md)
