---
title: "命名空間 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1f97b28bce20fa71f82942fa5f123d7c2ac6616a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="namespaces-entity-sql"></a>命名空間 (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 導入了命名空間來避免全域識別碼的名稱衝突，例如型別名稱、實體集、函式等等。 中的命名空間支援[!INCLUDE[esql](../../../../../../includes/esql-md.md)]中的命名空間支援類似[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)]。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供了兩種形式的 USING 子句：限定的命名空間 (為命名空間提供較短的別名) 及不限定的命名空間，如下列範例所述：  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>名稱解析規則  
 如果在本機的範圍，無法解析識別項[!INCLUDE[esql](../../../../../../includes/esql-md.md)]嘗試在全域範圍 （命名空間） 中找到的名稱。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會先嘗試將此識別項 (前置詞) 與其中一個限定的命名空間比對。 如果沒有相符項目，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]嘗試解析指定的命名空間中的識別項的其餘部分。 如果兩者不相符，則會擲回例外狀況。  
  
 下一步[!INCLUDE[esql](../../../../../../includes/esql-md.md)]嘗試搜尋所有非限定命名空間 （在初構中指定） 的識別項。 如果可以在剛好一個命名空間內找到此識別項，就會傳回該位置。 如果有一個以上的命名空間符合該識別項，則會擲回例外狀況。 如果沒有命名空間識別項，能夠識別[!INCLUDE[esql](../../../../../../includes/esql-md.md)]此名稱傳遞到下一個向外範圍 (<xref:System.Data.Common.DbCommand>或<xref:System.Data.Common.DbConnection>物件)，如下列範例所示：  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>與 .NET Framework 的差異  
 在 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 中，您可以使用部分限定的命名空間。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 則不允許。  
  
## <a name="adonet-usage"></a>ADO.NET 使用方式  
 查詢是透過 ADO.NET <xref:System.Data.Common.DbCommand> 物件來表示。 <xref:System.Data.Common.DbCommand> 物件則可經由 <xref:System.Data.Common.DbConnection> 物件建置。 此外，命名空間也可以指定成 <xref:System.Data.Common.DbCommand> 和 <xref:System.Data.Common.DbConnection> 物件的一部分。 如果[!INCLUDE[esql](../../../../../../includes/esql-md.md)]無法解析識別項，在查詢本身的外部命名空間會探查 （根據類似的規則）。  
  
## <a name="see-also"></a>請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
