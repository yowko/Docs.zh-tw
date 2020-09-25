---
title: 命名空間 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7a53f8e7e70dbc9fa505f7f8619af10a0e44c331
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197803"
---
# <a name="namespaces-entity-sql"></a>命名空間 (Entity SQL)

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 導入了命名空間來避免全域識別碼的名稱衝突，例如型別名稱、實體集、函式等等。 中的命名空間支援 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 類似于 .NET Framework 中的命名空間支援。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供了兩種形式的 USING 子句：限定的命名空間 (為命名空間提供較短的別名) 及不限定的命名空間，如下列範例所述：  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>名稱解析規則  

 如果識別碼無法在區域範圍中解析，則會 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 嘗試在全域範圍中找出 (命名空間) 的名稱。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會先嘗試將此識別項 (前置詞) 與其中一個限定的命名空間比對。 如果有相符的，則會 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 嘗試在指定的命名空間中解析識別碼的其餘部分。 如果兩者不相符，則會擲回例外狀況。  
  
 接著， [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 嘗試搜尋識別碼的初構) 中指定的所有非限定命名空間 (。 如果可以在剛好一個命名空間內找到此識別項，就會傳回該位置。 如果有一個以上的命名空間符合該識別項，則會擲回例外狀況。 如果找不到識別碼的命名空間，則會將 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 名稱傳遞到下一個範圍 (<xref:System.Data.Common.DbCommand> 或 <xref:System.Data.Common.DbConnection> 物件) ，如下列範例所示：  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>與 .NET Framework 的差異  

 在 .NET Framework 中，您可以使用部分限定的命名空間。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 則不允許。  
  
## <a name="adonet-usage"></a>ADO.NET 使用方式  

 查詢是透過 ADO.NET <xref:System.Data.Common.DbCommand> 物件來表示。 <xref:System.Data.Common.DbCommand> 物件則可經由 <xref:System.Data.Common.DbConnection> 物件建置。 此外，命名空間也可以指定成 <xref:System.Data.Common.DbCommand> 和 <xref:System.Data.Common.DbConnection> 物件的一部分。 如果 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 無法解析查詢本身內的識別碼，則會根據) 的類似規則 (探查外部命名空間。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [Entity SQL 概觀](entity-sql-overview.md)
