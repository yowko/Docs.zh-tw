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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c2a11ae83be1c7f75c5bc440c5f8162877106b07
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-return-rowsets"></a>如何：傳回資料列集
這個範例會從資料庫傳回資料列集 (Rowset)，並且包含用以篩選結果的輸入參數。  
  
 當您執行傳回資料列集的預存程序時，您會使用*結果*儲存從預存程序的類別。 如需詳細資訊，請參閱[分析 LINQ to SQL 原始程式碼](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md)。  
  
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
  
## <a name="see-also"></a>請參閱  
 [預存程序](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
