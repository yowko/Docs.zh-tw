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
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="1e977-102">作法：重複使用 ADO.NET 命令和 DataContext 之間的連接</span><span class="sxs-lookup"><span data-stu-id="1e977-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>

<span data-ttu-id="1e977-103">因為 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 是 ADO.NET 系列技術的一部分，而且是以 ADO.NET 提供的服務為基礎，所以您可以重複使用 ADO.NET 命令和之間的連接 <xref:System.Data.Linq.DataContext> 。</span><span class="sxs-lookup"><span data-stu-id="1e977-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the ADO.NET family of technologies and is based on services provided by ADO.NET, you can reuse a connection between an ADO.NET command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e977-104">範例</span><span class="sxs-lookup"><span data-stu-id="1e977-104">Example</span></span>  

 <span data-ttu-id="1e977-105">下列範例示範如何在 ADO.NET 命令和之間重複使用相同的連接 <xref:System.Data.Linq.DataContext> 。</span><span class="sxs-lookup"><span data-stu-id="1e977-105">The following example shows how to reuse the same connection between an ADO.NET command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="1e977-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e977-106">See also</span></span>

- [<span data-ttu-id="1e977-107">背景資訊</span><span class="sxs-lookup"><span data-stu-id="1e977-107">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="1e977-108">ADO.NET 和 LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1e977-108">ADO.NET and LINQ to SQL</span></span>](ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="1e977-109">與資料庫通訊</span><span class="sxs-lookup"><span data-stu-id="1e977-109">Communicating with the Database</span></span>](communicating-with-the-database.md)
