---
title: LINQ to SQL 查詢
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 534da029664af0babc3dff6226ff095b7222c34d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915840"
---
# <a name="linq-to-sql-queries"></a>LINQ to SQL 查詢
使用與 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 相同的語法，就可以定義 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 查詢。 唯一的差別在於查詢中參考的物件會對應至資料庫中的項目。 如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將您撰寫的查詢轉譯為對等 SQL 查詢，並將它們傳送給伺服器進行處理。 更精確的說，應用程式會使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API 來要求執行查詢。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 提供者接著會將查詢轉換為 SQL 文字，並將執行委派給 ADO 提供者。 而 ADO 提供者會將查詢結果傳回為 `DataReader`。 提供者會將 ADO 結果轉譯<xref:System.Linq.IQueryable>為使用者物件的集合。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
> [!NOTE]
> .NET Framework 內建型別的大部分方法和運算子都具有直接的翻譯至 SQL。 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 無法轉譯的部分則會產生執行階段例外狀況 (Exception)。 如需詳細資訊, 請參閱[SQL-CLR 型別對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)。  
  
 下表顯示 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 與 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢項目之間的相似及差異部分。  
  
|項目|LINQ 查詢|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢|  
|----------|----------------|----------------------------------------------------------------------|  
|保留查詢之區域變數的傳回型別 (適用於傳回序列的查詢)|泛型 `IEnumerable`|泛型 `IQueryable`|  
|指定資料來源|使用 (Visual Basic) 或`from` (C#) 子句`From`|相同|  
|篩選|`Where` 使用子句/ `where`|相同|  
|群組|`Group…By` 使用子句/ `groupby`|相同|  
|選取 (投影)|`Select` 使用子句/ `select`|相同|  
|延後執行與立即執行|請參閱[LINQ 查詢簡介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|相同|  
|實作聯結 (Join)|`Join` 使用子句/ `join`|`Join`可以使用/ <xref:System.Data.Linq.Mapping.AssociationAttribute>子句, 但更有效率地使用屬性。 `join` 如需詳細資訊, 請參閱[跨關聯性查詢](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md)。|  
|遠端執行與本機執行||如需詳細資訊, [請參閱 Remote vs。本機執行](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md)。|  
|資料流 (Streaming) 與快取查詢|不適用於本機記憶體案例||  
  
## <a name="see-also"></a>另請參閱

- [LINQ 查詢簡介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [基本 LINQ 查詢作業](../../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [LINQ 查詢作業中的型別關聯性](../../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
