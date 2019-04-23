---
title: HOW TO：傳回資料列集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: 599ad6f722251003ab56547ce050cbd0e8da831d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168710"
---
# <a name="how-to-return-rowsets"></a>HOW TO：傳回資料列集
這個範例會從資料庫傳回資料列集 (Rowset)，並且包含用以篩選結果的輸入參數。  
  
 當您執行傳回資料列集的預存程序時，您會使用*結果*類別，以儲存從預存程序傳回。 如需詳細資訊，請參閱 <<c0> [ 分析的 LINQ to SQL 原始程式碼](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md)。  
  
## <a name="example"></a>範例  
 下列範例表示一個預存程序，該程序會傳回客戶資料列並使用輸入參數，以便只傳回將 "London" 列為客戶所在城市的那些資料列。 此範例假設了一個可列舉的 `CustomersByCityResult` 類別。  
  
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
  
## <a name="see-also"></a>另請參閱

- [預存程序](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
- [下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
