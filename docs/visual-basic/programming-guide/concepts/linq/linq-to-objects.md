---
title: LINQ to Objects (Visual Basic)
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: c1e2e8fbaaf984fec69322a459fc7c55890965ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326875"
---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
詞彙 "LINQ to Objects" 是指直接搭配使用 LINQ 查詢與任何 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601> 集合，而不要使用中繼 LINQ 提供者或 API (例如 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) 或 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md))。 您可以使用 LINQ 查詢任何可列舉的集合，例如 <xref:System.Collections.Generic.List%601>、<xref:System.Array> 或 <xref:System.Collections.Generic.Dictionary%602>。 這類集合可以是使用者定義，或由 .NET Framework API 所傳回。  
  
 基本上，LINQ to Objects 代表使用集合的新方法。 在舊的方法中，您必須撰寫複雜的 `For Each` 迴圈，以指定如何從集合擷取資料。 在 LINQ 方法中，您會撰寫描述所要擷取內容的宣告式程式碼。  
  
 此外，LINQ 查詢還提供三種超越傳統 `For Each` 迴圈的主要優點：  
  
1. 它們更加簡潔易懂 (尤其是在篩選多個條件時)。  
  
2. 它們只要使用最少的應用程式程式碼，即可提供強大的篩選、排序及群組功能。  
  
3. 它們只需要一點修改，甚至不用修改，便可以移植到其他資料來源。  
  
 一般來說，您要對資料執行的作業越複雜，就越能體會使用 LINQ 取代傳統反覆項目技術的好處。  
  
 本節的目的是要透過一些精選的範例，示範 LINQ 方法， 而不是要提供詳細的說明。  
  
## <a name="in-this-section"></a>本節內容  
 [LINQ 和字串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 說明如何使用 LINQ 查詢及轉換字串與字串集合。 此外也包含示範這些原理的主題連結。  
  
 [LINQ 和反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 示範 LINQ 如何使用反映的範例連結。  
  
 [LINQ 與檔案目錄 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 說明如何使用 LINQ 與檔案系統互動。 此外也包含示範這些概念的主題連結。  
  
 [如何：使用 LINQ (Visual Basic) 查詢 ArrayList](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 示範如何以 C# 查詢 ArrayList。  
  
 [如何：新增自訂方法的 LINQ 查詢 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 說明如何透過將擴充方法加入至 <xref:System.Collections.Generic.IEnumerable%601> 介面，來延伸您可以用於 LINQ 查詢的方法組。  
  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 提供 LINQ 的主題說明連結，以及執行查詢的程式碼範例。
