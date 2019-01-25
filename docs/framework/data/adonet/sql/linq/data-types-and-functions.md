---
title: 資料類型與函式
ms.date: 03/30/2017
ms.assetid: 683413c5-0312-4e60-8619-9a97bdc6e62a
ms.openlocfilehash: 0a60c5f680937816cd97b4ef44ee7fd1ad510f73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711891"
---
# <a name="data-types-and-functions"></a>資料類型與函式
下表所列的主題將針對 Common Language Runtime (CLR) 的成員、建構和轉換描述 LINQ to SQL 支援。 支援的成員和建構可用於您的 LINQ to SQL 查詢中。  
  
 此表中不支援的項目表示 LINQ to SQL 無法轉譯 CLR 成員、建構或轉換，以便在 SQL Server 上執行。 雖然您仍然可以在程式碼中使用它們，但是必須在查詢轉譯成 Transact-SQL 之前或從資料庫中擷取結果之後，評估這些項目。  
  
|主題|描述|  
|-----------|-----------------|  
|[SQL-CLR 類型對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)|提供 CLR 型別和 SQL Server 型別間之對應的詳細對照表。|  
|[基本資料類型](../../../../../../docs/framework/data/adonet/sql/linq/basic-data-types.md)|摘要列出與 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 之間的行為差異。|  
|[Boolean 資料類型](../../../../../../docs/framework/data/adonet/sql/linq/boolean-data-types.md)|摘要列出與 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 之間的行為差異。|  
|[Null 語意](../../../../../../docs/framework/data/adonet/sql/linq/null-semantics.md)|提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 主題的連結，而這些主題是討論 Null 和可為 Null 的問題。|  
|[數值和比較運算子](../../../../../../docs/framework/data/adonet/sql/linq/numeric-and-comparison-operators.md)|摘要列出與 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 之間的行為差異。|  
|[序列運算子](../../../../../../docs/framework/data/adonet/sql/linq/sequence-operators.md)|摘要列出與 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 之間的行為差異。|  
|[System.Convert 方法](../../../../../../docs/framework/data/adonet/sql/linq/system-convert-methods.md)|摘要列出與 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 之間的行為差異。|  
|[System.DateTime 方法](../../../../../../docs/framework/data/adonet/sql/linq/system-datetime-methods.md)|描述 LINQ to SQL 對 <xref:System.DateTime?displayProperty=nameWithType> 結構之成員的支援。|  
|[System.DateTimeOffset 方法](../../../../../../docs/framework/data/adonet/sql/linq/system-datetimeoffset-methods.md)|描述 LINQ to SQL 對 <xref:System.DateTimeOffset?displayProperty=nameWithType> 結構之成員的支援。|  
|[System.Math 方法](../../../../../../docs/framework/data/adonet/sql/linq/system-math-methods.md)|摘要列出與 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 之間的行為差異。|  
|[System.Object 方法](../../../../../../docs/framework/data/adonet/sql/linq/system-object-methods.md)|摘要列出與 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 之間的行為差異。|  
|[System.String 方法](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|摘要列出與 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 之間的行為差異。|  
|[System.TimeSpan 方法](../../../../../../docs/framework/data/adonet/sql/linq/system-timespan-methods.md)|描述 LINQ to SQL 對 <xref:System.TimeSpan?displayProperty=nameWithType> 結構之成員的支援。|  
|[不支援的功能](../../../../../../docs/framework/data/adonet/sql/linq/unsupported-functionality.md)|描述 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中不支援的功能。|  
  
## <a name="see-also"></a>另請參閱
- [SQL-CLR 類型不符](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)
- [參考資料](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [在 Visual Studio 中的.NET framework 類別庫](https://msdn.microsoft.com/library/a03e374c-3d5c-4169-937b-49857ab273ae)
