---
title: HOW TO：重複使用 ADO.NET 命令和 DataContext 之間的連接
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 47e1e45cfe693e3569c343f1058ce2d610af96dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163146"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="b23ab-102">HOW TO：重複使用 ADO.NET 命令和 DataContext 之間的連接</span><span class="sxs-lookup"><span data-stu-id="b23ab-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>
<span data-ttu-id="b23ab-103">因為[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]屬於[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)]技術家族的且根據所提供的服務[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)]，您可以重複使用之間的連線[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)]命令和<xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="b23ab-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] family of technologies and is based on services provided by [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], you can reuse a connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b23ab-104">範例</span><span class="sxs-lookup"><span data-stu-id="b23ab-104">Example</span></span>  
 <span data-ttu-id="b23ab-105">下列範例會顯示如何重複使用介於 [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] 命令和 <xref:System.Data.Linq.DataContext> 之間的相同連接。</span><span class="sxs-lookup"><span data-stu-id="b23ab-105">The following example shows how to reuse the same connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b23ab-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b23ab-106">See also</span></span>

- [<span data-ttu-id="b23ab-107">背景資訊</span><span class="sxs-lookup"><span data-stu-id="b23ab-107">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="b23ab-108">ADO.NET 和 LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b23ab-108">ADO.NET and LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="b23ab-109">與資料庫通訊</span><span class="sxs-lookup"><span data-stu-id="b23ab-109">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
