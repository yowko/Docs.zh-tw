---
title: 如何：顯示產生的 SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: edc0f8fea2768391a47e12940cbe083e41852f1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361704"
---
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="1244c-102">如何：顯示產生的 SQL</span><span class="sxs-lookup"><span data-stu-id="1244c-102">How to: Display Generated SQL</span></span>
<span data-ttu-id="1244c-103">您可以檢視針對查詢所產生的 SQL 程式碼，並且使用 <xref:System.Data.Linq.DataContext.Log%2A> 屬性變更處理。</span><span class="sxs-lookup"><span data-stu-id="1244c-103">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="1244c-104">若要了解 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 功能以及對特定問題進行偵錯，這個方法很實用。</span><span class="sxs-lookup"><span data-stu-id="1244c-104">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1244c-105">範例</span><span class="sxs-lookup"><span data-stu-id="1244c-105">Example</span></span>  
 <span data-ttu-id="1244c-106">下列範例會使用 <xref:System.Data.Linq.DataContext.Log%2A> 屬性，在執行 SQL 程式碼之前，於主控台視窗中顯示該程式碼。</span><span class="sxs-lookup"><span data-stu-id="1244c-106">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="1244c-107">您可以使用這個屬性搭配查詢、插入、更新和刪除命令。</span><span class="sxs-lookup"><span data-stu-id="1244c-107">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="1244c-108">在主控台視窗中的程式行是執行 Visual Basic 或 C# 程式碼所示時看到的內容。</span><span class="sxs-lookup"><span data-stu-id="1244c-108">The lines from the console window are what you see when you execute the Visual Basic or C# code that follows.</span></span>  
  
```  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1244c-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1244c-109">See Also</span></span>  
 [<span data-ttu-id="1244c-110">偵錯支援</span><span class="sxs-lookup"><span data-stu-id="1244c-110">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
