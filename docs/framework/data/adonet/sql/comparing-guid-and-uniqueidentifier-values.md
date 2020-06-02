---
title: 比較 GUID 和 uniqueidentifier 值
description: 瞭解如何在 .NET Framework Data Provider 中建立及比較 SQL Server 的 GUID 值，這是由 uniqueidentifier 資料型別所代表。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: 245b7246712822043d302c43a765c29ac2090e00
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286503"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>比較 GUID 和 uniqueidentifier 值
SQL Server 中的全域唯一識別碼 (GUID) 資料類型會以 `uniqueidentifier` 資料類型來表示，它會儲存 16 位元組的二進位值。 GUID 是二進位數字，主要當成識別項使用，在許多電腦位於許多站台上的網路中，該識別項必須是唯一的。 GUID 可藉由呼叫 Transact-SQL NEWID 函數來產生，並保證在全世界都是唯一的。 如需詳細資訊，請參閱 [uniqueidentifier (Transact-SQL)](/sql/t-sql/data-types/uniqueidentifier-transact-sql)。  
  
## <a name="working-with-sqlguid-values"></a>使用 SqlGuid 值  
 由於 GUID 值很長且難理解，因此它們對使用者而言不具任何意義。 如果會針對索引鍵值使用隨機產生的 GUID，而且您插入了大量資料列，則您會在索引中取得隨機的 I/O，這可能會對效能產生負面影響。 相較於其他資料類型，GUID 也相對較大。 一般來說，我們建議僅針對範圍非常侷限且不適用其他資料類型的案例使用 GUID。  
  
### <a name="comparing-guid-values"></a>比較 GUID 值  
 比較運算子可以搭配使用 `uniqueidentifier` 值。 不過排序並不是比較兩值的位元模式加以實作的。 對值所允許的唯一作業 `uniqueidentifier` 是比較（=、 <>、 \<, > 、 \<=, > =）及檢查 Null （IS Null 和 is NOT null）。 不允許其他算術運算子。  
  
 <xref:System.Guid> 和 <xref:System.Data.SqlTypes.SqlGuid> 都具有 `CompareTo` 方法，可用來比較不同的 GUID 值。 不過，`System.Guid.CompareTo` 和 `SqlTypes.SqlGuid.CompareTo` 的實作方式不同。 <xref:System.Data.SqlTypes.SqlGuid> 會使用 SQL Server 行為來實作 `CompareTo`，值的最後六個位元組最重要。 <xref:System.Guid> 會評估所有的 16 個位元組。 下列範例示範這項行為差異。 程式碼的第一個區段會顯示未排序的 <xref:System.Guid> 值，而程式碼的第二個區段會顯示已排序的 <xref:System.Guid> 值。 第三個區段則會顯示已排序的 <xref:System.Data.SqlTypes.SqlGuid> 值。 輸出會顯示於程式碼清單下方。  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 這個範例會產生下列結果。  
  
```output  
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

- [SQL Server 資料類型和 ADO.NET](sql-server-data-types.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
