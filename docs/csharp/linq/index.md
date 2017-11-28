---
title: Language Integrated Query (LINQ)
description: "介紹使用 C# 的 Language Integrated Query (LINQ)"
keywords: .NET, .NET Core, LINQ, C#
author: BillWagner
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 007cc736-f5cf-4919-b99b-0c00ab2814ce
ms.openlocfilehash: c4c26e2b7b0693ec940958a9b7d2d306001090e7
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="language-integrated-query-linq"></a>Language Integrated Query (LINQ)

Language Integrated Query (LINQ) 是一組以直接將查詢功能整合至 C# 語言為基礎之技術的名稱。 傳統上，針對資料的查詢是以簡單字串表示，而不會在編譯期間進行型別檢查，或提供 IntelliSense 支援。 此外，您必須針對每個資料來源型別 (例如 SQL 資料庫、XML 文件、各種 Web 服務等等) 學習不同的查詢語言。 透過 LINQ，查詢會是第一級語言建構，和類別、方法及事件相同。

對於撰寫查詢的開發人員來說，LINQ 最明顯的「語言整合」部分就是查詢運算式。 查詢運算式是以宣告式「查詢語法」撰寫。 透過使用查詢語法，您就可以利用最少的程式碼，針對資料來源執行篩選、排序及分組作業。 您可以使用相同的基本查詢運算式模式，來查詢並轉換 SQL 資料庫、ADO .NET 資料集、XML 文件及資料流，以及 .NET 集合中的資料。

下列範例示範完整的查詢作業。 完整的作業包括建立資料來源、定義查詢運算式，並在 `foreach` 陳述式中執行查詢。

[!code-csharp[csProgGuideLINQ#11](../../../samples/snippets/csharp/concepts/linq/index_1.cs)]

## <a name="query-expression-overview"></a>查詢運算式概觀

-   查詢運算式可以用來查詢並轉換來自任何已啟用 LINQ 之資料來源的資料。 例如，單一查詢可以從 SQL 資料庫擷取資料，並產生 XML 資料流做為輸出。  
  
-   查詢運算式很容易學習，因為其中使用許多熟悉的 C# 語言建構。  
  
-   查詢運算式中的變數皆為強型別，不過您在很多情況下並不需要明確提供型別，因為編譯器能夠自行推斷它。 如需詳細資訊，請參閱 [LINQ 查詢作業中的型別關聯性](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。  
  
-   在您針對查詢變數進行逐一查看之前 (例如，在 `foreach` 陳述式中)，查詢將不會執行。 如需詳細資訊，請參閱 [LINQ 查詢簡介](../programming-guide/concepts/linq/introduction-to-linq-queries.md)。  
  
-   在編譯期間，查詢運算式會根據 C# 規格中提出的規則，轉換成「標準查詢運算子」方法呼叫。 所有可使用查詢語法表示的查詢，也都可以利用方法語法來表示。 不過，在大多數情況下，查詢語法較容易閱讀且更簡潔。 如需詳細資訊，請參閱 [C# 語言規格](../language-reference/language-specification/index.md)和[標準查詢運算子概觀](../programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
-   做為撰寫 LINQ 查詢的規則，我們建議您優先使用查詢語法，且只有在必要時才使用方法語法。 這兩個形式之間並沒有語意或效能上的差異。 相較於以方法語法撰寫的對等運算式，查詢運算式通常更容易閱讀。  
  
-   某些查詢作業 (例如 <xref:System.Linq.Enumerable.Count%2A> 或 <xref:System.Linq.Enumerable.Max%2A>) 沒有同等的查詢運算式子句，因此必須以方法呼叫來表示。 方法語法能以數種方式來與查詢語法結合。 如需詳細資訊，請參閱 [LINQ 中的查詢語法和方法語法](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)。  
  
-   根據查詢所套用的型別，可將查詢運算式編譯為運算式樹狀結構或委派。 <xref:System.Collections.Generic.IEnumerable%601> 查詢會編譯成委派。 <xref:System.Linq.IQueryable> 和 <xref:System.Linq.IQueryable%601> 查詢會編譯成運算式樹狀架構。 如需詳細資訊，請參閱[運算式樹狀結構](../expression-trees.md)。  

## <a name="next-steps"></a>後續步驟

若要深入了解 LINQ 的詳細資料，請先參閱[查詢運算式基本概念](query-expression-basics.md)以熟悉基本概念，然後閱讀您感興趣的 LINQ 技術文件：   
-   XML 文件：[LINQ to XML](../programming-guide/concepts/linq/linq-to-xml.md)  
  
-   ADO.NET Entity Framework：[LINQ to Entities](../../framework/data/adonet/ef/language-reference/linq-to-entities.md)  
  
-   .NET 集合、檔案、字串等等：[LINQ to Objects](../programming-guide/concepts/linq/linq-to-objects.md)

若要深入了解 LINQ 的一般資訊，請參閱 [C# 中的 LINQ](linq-in-csharp.md)。

若要開始使用 C# 中的 LINQ，請參閱[使用 LINQ](../tutorials/working-with-linq.md) 教學課程。


