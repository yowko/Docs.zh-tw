---
title: 如何：重複使用 ADO.NET 命令和 DataContext 之間的連接
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 9618ffd3f6b1a050a4c47d1912b4612ce4031cd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352944"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>如何：重複使用 ADO.NET 命令和 DataContext 之間的連接
因為[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]屬於[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)]技術家族的並且根據所提供的服務[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)]，您可以重複使用之間的連線[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)]命令和<xref:System.Data.Linq.DataContext>。  
  
## <a name="example"></a>範例  
 下列範例會顯示如何重複使用介於 [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] 命令和 <xref:System.Data.Linq.DataContext> 之間的相同連接。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>另請參閱  
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [ADO.NET 和 LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)  
 [與資料庫通訊](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
