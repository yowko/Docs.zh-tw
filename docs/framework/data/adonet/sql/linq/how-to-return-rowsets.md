---
title: 作法：傳回資料列集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: 5ec188e0345140297062d0a10dfbbc4a294bbb7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781604"
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="44b36-102">HOW TO：傳回資料列集</span><span class="sxs-lookup"><span data-stu-id="44b36-102">How to: Return Rowsets</span></span>
<span data-ttu-id="44b36-103">這個範例會從資料庫傳回資料列集 (Rowset)，並且包含用以篩選結果的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="44b36-103">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="44b36-104">當您執行會傳回資料列集的預存程式時，您會使用*結果*類別來儲存預存程式的傳回。</span><span class="sxs-lookup"><span data-stu-id="44b36-104">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="44b36-105">如需詳細資訊，請參閱[分析 LINQ to SQL 原始碼](analyzing-linq-to-sql-source-code.md)。</span><span class="sxs-lookup"><span data-stu-id="44b36-105">For more information, see [Analyzing LINQ to SQL Source Code](analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44b36-106">範例</span><span class="sxs-lookup"><span data-stu-id="44b36-106">Example</span></span>  
 <span data-ttu-id="44b36-107">下列範例表示一個預存程序，該程序會傳回客戶資料列並使用輸入參數，以便只傳回將 "London" 列為客戶所在城市的那些資料列。</span><span class="sxs-lookup"><span data-stu-id="44b36-107">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="44b36-108">此範例假設了一個可列舉的 `CustomersByCityResult` 類別。</span><span class="sxs-lookup"><span data-stu-id="44b36-108">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44b36-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44b36-109">See also</span></span>

- [<span data-ttu-id="44b36-110">預存程序</span><span class="sxs-lookup"><span data-stu-id="44b36-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="44b36-111">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="44b36-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
