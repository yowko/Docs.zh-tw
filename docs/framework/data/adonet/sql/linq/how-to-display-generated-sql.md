---
title: 作法：顯示產生的 SQL
description: 瞭解如何使用 Log 屬性來查看針對查詢所產生的 SQL 程式碼，以協助瞭解 LINQ to SQL 功能和進行偵錯工具。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: 81f6b9603cc7f8b7863f787272ce6a1af920fa75
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169475"
---
# <a name="how-to-display-generated-sql"></a>作法：顯示產生的 SQL

您可以檢視針對查詢所產生的 SQL 程式碼，並且使用 <xref:System.Data.Linq.DataContext.Log%2A> 屬性變更處理。 若要了解 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 功能以及對特定問題進行偵錯，這個方法很實用。  
  
## <a name="example"></a>範例  

 下列範例會使用 <xref:System.Data.Linq.DataContext.Log%2A> 屬性，在執行 SQL 程式碼之前，於主控台視窗中顯示該程式碼。  您可以使用這個屬性搭配查詢、插入、更新和刪除命令。  
  
 主控台視窗中的程式列就是您在執行下列 Visual Basic 或 c # 程式碼時所看到的內容。  
  
```console  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```console  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯支援](debugging-support.md)
