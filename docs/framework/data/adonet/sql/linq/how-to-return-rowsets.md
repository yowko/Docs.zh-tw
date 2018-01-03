---
title: "如何：傳回資料列集"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c5f88ce69239c0ca601344362dc420205291cb74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="6ea71-102">如何：傳回資料列集</span><span class="sxs-lookup"><span data-stu-id="6ea71-102">How to: Return Rowsets</span></span>
<span data-ttu-id="6ea71-103">這個範例會從資料庫傳回資料列集 (Rowset)，並且包含用以篩選結果的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="6ea71-103">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="6ea71-104">當您執行傳回資料列集的預存程序時，您會使用*結果*儲存從預存程序的類別。</span><span class="sxs-lookup"><span data-stu-id="6ea71-104">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="6ea71-105">如需詳細資訊，請參閱[分析 LINQ to SQL 原始程式碼](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md)。</span><span class="sxs-lookup"><span data-stu-id="6ea71-105">For more information, see [Analyzing LINQ to SQL Source Code](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ea71-106">範例</span><span class="sxs-lookup"><span data-stu-id="6ea71-106">Example</span></span>  
 <span data-ttu-id="6ea71-107">下列範例表示一個預存程序，該程序會傳回客戶資料列並使用輸入參數，以便只傳回將 "London" 列為客戶所在城市的那些資料列。</span><span class="sxs-lookup"><span data-stu-id="6ea71-107">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="6ea71-108">此範例假設了一個可列舉的 `CustomersByCityResult` 類別。</span><span class="sxs-lookup"><span data-stu-id="6ea71-108">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
```  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6ea71-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="6ea71-109">See Also</span></span>  
 [<span data-ttu-id="6ea71-110">預存程序</span><span class="sxs-lookup"><span data-stu-id="6ea71-110">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [<span data-ttu-id="6ea71-111">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="6ea71-111">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
