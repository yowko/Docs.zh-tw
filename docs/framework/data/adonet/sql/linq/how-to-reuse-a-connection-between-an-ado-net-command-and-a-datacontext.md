---
title: HOW TO：重複使用 ADO.NET 命令和 DataContext 之間的連接
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 92b0d8cf2c4904fabc17241ef2c31175f0c87baf
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878542"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="6cf6f-102">作法：重複使用 ADO.NET 命令和 DataContext 之間的連接</span><span class="sxs-lookup"><span data-stu-id="6cf6f-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>
<span data-ttu-id="6cf6f-103">因為[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]是屬於 ADO.NET 系列的技術，並提供 ado.net，您可以重複使用 ADO.NET 命令之間的連線，根據服務和<xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="6cf6f-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the ADO.NET family of technologies and is based on services provided by ADO.NET, you can reuse a connection between an ADO.NET command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cf6f-104">範例</span><span class="sxs-lookup"><span data-stu-id="6cf6f-104">Example</span></span>  
 <span data-ttu-id="6cf6f-105">下列範例示範如何重複使用相同的連接之間 ADO.NET 命令和<xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="6cf6f-105">The following example shows how to reuse the same connection between an ADO.NET command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6cf6f-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cf6f-106">See also</span></span>

- [<span data-ttu-id="6cf6f-107">背景資訊</span><span class="sxs-lookup"><span data-stu-id="6cf6f-107">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="6cf6f-108">ADO.NET 和 LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6cf6f-108">ADO.NET and LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="6cf6f-109">與資料庫通訊</span><span class="sxs-lookup"><span data-stu-id="6cf6f-109">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
