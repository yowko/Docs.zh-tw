---
title: 比較 GUID 和 uniqueidentifier 值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: 7d982b73332a2629ccd32c409e0de6fe1ce6eb98
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556301"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>比較 GUID 和 uniqueidentifier 值
SQL Server 中的全域唯一識別碼 (GUID) 資料型別由 `uniqueidentifier` 資料型別所表示，其儲存 16 個位元組的二進位值。 GUID 是二進位數字，主要當成識別項使用，在許多電腦位於許多站台上的網路中，該識別項必須是唯一的。 可藉由呼叫 Transact-SQL NEWID 函式的方法來產生 GUID，並保證此 GUID 是全球唯一的。 如需詳細資訊，請參閱 < [uniqueidentifier & Amp;#40;transact-SQL&AMP;#41;](/sql/t-sql/data-types/uniqueidentifier-transact-sql)。  
  
## <a name="working-with-sqlguid-values"></a>使用 SqlGuid 值  
 GUID 值又長又難以理解，對使用者而言不具任何意義。 如果將隨機產生的 GUID 用於索引鍵值，且插入大量資料列，則會使隨機 I/O 進入索引，進而對效能產生負面影響。 而且相較之下，GUID 比其他資料型別還要大。 因此，一般建議僅在其他資料型別都不適用的極少案例中，才使用 GUID。  
  
### <a name="comparing-guid-values"></a>比較 GUID 值  
 比較運算子可以與 `uniqueidentifier` 值搭配使用。 不過，比較這兩個值的位元模式並不會實作排序作業。 唯一允許的作業`uniqueidentifier`值是比較 (=、 <>， \<，>， \<=、 > =) 以及檢查 NULL （IS NULL 和 IS NOT NULL）。 而不允許其他算術運算子。  
  
 <xref:System.Guid> 及 <xref:System.Data.SqlTypes.SqlGuid> 都具有可用來比較不同 GUID 值的 `CompareTo` 方法。 但是，`System.Guid.CompareTo` 和 `SqlTypes.SqlGuid.CompareTo` 的實作方式不同。 <xref:System.Data.SqlTypes.SqlGuid> 會使用 SQL Server 行為來實作 `CompareTo`，而值的最後 6 個位元組是最重要的。 而 <xref:System.Guid> 則 16 個位元組全都評估。 下列範例示範此行為差異。 程式碼的第一個區段顯示未排序的 <xref:System.Guid> 值，第二個區段顯示已排序的 <xref:System.Guid> 值。 第三區段則顯示已排序的 <xref:System.Data.SqlTypes.SqlGuid> 值。 而輸出則顯示在程式碼清單下面。  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 此範例會產生下列結果。  
  
```  
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## <a name="see-also"></a>另請參閱  

[SQL Server 資料類型和 ADO.NET](sql-server-data-types.md)  
[ADO.NET 概觀](../ado-net-overview.md)  
