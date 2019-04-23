---
title: LINQ to SQL 查詢
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 49106502dc58eef36ea0c910c627c9cf397f419e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076181"
---
# <a name="linq-to-sql-queries"></a>LINQ to SQL 查詢
使用與 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 相同的語法，就可以定義 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 查詢。 唯一的差別在於查詢中參考的物件會對應至資料庫中的項目。 如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將您撰寫的查詢轉譯為對等 SQL 查詢，並將它們傳送給伺服器進行處理。 更精確的說，應用程式會使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API 來要求執行查詢。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 提供者接著會將查詢轉換為 SQL 文字，並將執行委派給 ADO 提供者。 而 ADO 提供者會將查詢結果傳回為 `DataReader`。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]提供者會將轉譯將 ADO 結果<xref:System.Linq.IQueryable>使用者物件的集合。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 內建型別的大部分方法和運算子都可以直接轉譯為 SQL。 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 無法轉譯的部分則會產生執行階段例外狀況 (Exception)。 如需詳細資訊，請參閱 < [SQL-CLR 類型對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)。  
  
 下表顯示 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 與 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢項目之間的相似及差異部分。  
  
|項目|LINQ 查詢|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢|  
|----------|----------------|----------------------------------------------------------------------|  
|保留查詢之區域變數的傳回型別 (適用於傳回序列的查詢)|泛型 `IEnumerable`|泛型 `IQueryable`|  
|指定資料來源|會使用`From`(Visual Basic) 或`from`(C#) 子句|相同|  
|篩選|會使用`Where` / `where`子句|相同|  
|群組|會使用`Group…By` / `groupby`子句|相同|  
|選取 (投影)|會使用`Select` / `select`子句|相同|  
|延後執行與立即執行|請參閱[LINQ 查詢簡介 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|相同|  
|實作聯結 (Join)|會使用`Join` / `join`子句|可以使用`Join` / `join`子句，但更有效率地使用<xref:System.Data.Linq.Mapping.AssociationAttribute>屬性。 如需詳細資訊，請參閱 <<c0> [ 跨關聯性查詢](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md)。|  
|遠端執行與本機執行||如需詳細資訊，請參閱[遠端與。本機執行](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md)。|  
|資料流 (Streaming) 與快取查詢|不適用於本機記憶體案例||  
  
## <a name="see-also"></a>另請參閱

- [LINQ 查詢簡介 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [基本 LINQ 查詢作業](~/docs/csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [LINQ 查詢作業中的型別關聯性](~/docs/csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
