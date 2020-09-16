---
title: LINQ to Objects (C#)
description: '深入瞭解 c # 中的 LINQ to Objects，其 <T> 會在沒有中繼 LINQ 提供者或 API 的情況下，使用具有任何 IEnumerable 或 ienumerable 集合的 LINQ 查詢。'
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: f8e65f129dc002d9615b01e3a3a123514754b886
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557002"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)

詞彙 "LINQ to Objects" 是指直接搭配使用 LINQ 查詢與任何 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601> 集合，而不要使用中繼 LINQ 提供者或 API (例如 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) 或 [LINQ to XML](../../../../standard/linq/linq-xml-overview.md))。 您可以使用 LINQ 查詢任何可列舉的集合，例如 <xref:System.Collections.Generic.List%601>、<xref:System.Array> 或 <xref:System.Collections.Generic.Dictionary%602>。 集合可能是使用者定義的，也可能是由 .NET API 傳回。  
  
 基本上，LINQ to Objects 代表使用集合的新方法。 在舊的方法中，您必須撰寫複雜的 `foreach` 迴圈，以指定如何從集合擷取資料。 在 LINQ 方法中，您會撰寫描述所要擷取內容的宣告式程式碼。  
  
 此外，LINQ 查詢還提供三種超越傳統 `foreach` 迴圈的主要優點：  
  
- 它們更加簡潔易懂 (尤其是在篩選多個條件時)。  
  
- 它們只要使用最少的應用程式程式碼，即可提供強大的篩選、排序及群組功能。  
  
- 它們只需要一點修改，甚至不用修改，便可以移植到其他資料來源。  
  
 一般來說，您想要對資料執行的作業越複雜，您就可以使用 LINQ 而不是傳統的反復專案技術來實現更多好處。  
  
 本節的目的是要透過一些精選的範例，示範 LINQ 方法， 這並非詳盡的設計。  
  
## <a name="in-this-section"></a>本節內容  
 [LINQ 和字串 (C#)](./linq-and-strings.md)  
 說明如何使用 LINQ 查詢及轉換字串與字串集合。 也包含示範這些原則的文章連結。  
  
 [LINQ 和反映 (C#)](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 示範 LINQ 如何使用反映的範例連結。  
  
 [LINQ 和檔案目錄 (C#)](./linq-and-file-directories.md)  
 說明如何使用 LINQ 與檔案系統互動。 也包含示範這些概念的文章連結。  
  
 [如何使用 LINQ (c # ) 查詢 ArrayList ](./how-to-query-an-arraylist-with-linq.md)  
 示範如何以 C# 查詢 ArrayList。  
  
 [如何新增 LINQ 查詢的自訂方法 (c # ) ](./how-to-add-custom-methods-for-linq-queries.md)  
 說明如何透過將擴充方法加入至 <xref:System.Collections.Generic.IEnumerable%601> 介面，來延伸您可以用於 LINQ 查詢的方法組。  
  
 [Language-Integrated Query (LINQ) (C#)](./index.md)  
 提供文章的連結，說明 LINQ 並提供執行查詢的程式碼範例。
