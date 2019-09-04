---
title: 資料類型與函式
ms.date: 03/30/2017
ms.assetid: 683413c5-0312-4e60-8619-9a97bdc6e62a
ms.openlocfilehash: 864c3a4668e3a405260d897596c4e94cc83419a8
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247216"
---
# <a name="data-types-and-functions"></a>資料類型與函式
下表所列的主題將針對 Common Language Runtime (CLR) 的成員、建構和轉換描述 LINQ to SQL 支援。 支援的成員和建構可用於您的 LINQ to SQL 查詢中。  
  
 此表中不支援的項目表示 LINQ to SQL 無法轉譯 CLR 成員、建構或轉換，以便在 SQL Server 上執行。 雖然您仍然可以在程式碼中使用它們，但是必須在查詢轉譯成 Transact-SQL 之前或從資料庫中擷取結果之後，評估這些項目。  
  
|主題|描述|  
|-----------|-----------------|  
|[SQL-CLR 類型對應](sql-clr-type-mapping.md)|提供 CLR 型別和 SQL Server 型別間之對應的詳細對照表。|  
|[基本資料類型](basic-data-types.md)|摘要說明 .NET Framework 的行為差異。|  
|[Boolean 資料類型](boolean-data-types.md)|摘要說明 .NET Framework 的行為差異。|  
|[Null 語意](null-semantics.md)|提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 主題的連結，而這些主題是討論 Null 和可為 Null 的問題。|  
|[數值和比較運算子](numeric-and-comparison-operators.md)|摘要說明 .NET Framework 的行為差異。|  
|[序列運算子](sequence-operators.md)|摘要說明 .NET Framework 的行為差異。|  
|[System.Convert 方法](system-convert-methods.md)|摘要說明 .NET Framework 的行為差異。|  
|[System.DateTime 方法](system-datetime-methods.md)|描述 LINQ to SQL 對 <xref:System.DateTime?displayProperty=nameWithType> 結構之成員的支援。|  
|[System.DateTimeOffset 方法](system-datetimeoffset-methods.md)|描述 LINQ to SQL 對 <xref:System.DateTimeOffset?displayProperty=nameWithType> 結構之成員的支援。|  
|[System.Math 方法](system-math-methods.md)|摘要說明 .NET Framework 的行為差異。|  
|[System.Object 方法](system-object-methods.md)|摘要說明 .NET Framework 的行為差異。|  
|[System.String 方法](system-string-methods.md)|摘要說明 .NET Framework 的行為差異。|  
|[System.TimeSpan 方法](system-timespan-methods.md)|描述 LINQ to SQL 對 <xref:System.TimeSpan?displayProperty=nameWithType> 結構之成員的支援。|  
|[不支援的功能](unsupported-functionality.md)|描述 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中不支援的功能。|  
  
## <a name="see-also"></a>另請參閱

- [SQL-CLR 類型不符](sql-clr-type-mismatches.md)
- [參考資料](reference.md)
