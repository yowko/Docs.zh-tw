---
title: "LINQ to Objects (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d2bc048fea9affd4998430783d20b978317f3897
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
詞彙 「 LINQ 到物件 」 指的是使用 LINQ 查詢與任何<xref:System.Collections.IEnumerable>或<xref:System.Collections.Generic.IEnumerable%601>集合，而不使用中繼的 LINQ 提供者或 API，例如[LINQ to SQL](https://msdn.microsoft.com/library/bb386976)或[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)。</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable> 您可以使用 LINQ 來查詢任何可列舉集合，例如<xref:System.Collections.Generic.List%601>， <xref:System.Array>，或<xref:System.Collections.Generic.Dictionary%602>.</xref:System.Collections.Generic.Dictionary%602> </xref:System.Array> </xref:System.Collections.Generic.List%601> 可能是使用者定義的集合，或可能傳回的.NET Framework API。  
  
 基本上，LINQ to Objects 代表集合的新方法。 在舊的方法中，您必須撰寫複雜的 `For Each` 迴圈，以指定如何從集合擷取資料。 在 LINQ 方法中，您可以撰寫描述您想要擷取的宣告式程式碼。  
  
 此外，LINQ 查詢提供三個主要的好處，超越傳統`For Each`迴圈︰  
  
1.  它們更加簡潔易懂 (尤其是在篩選多個條件時)。  
  
2.  它們只要使用最少的應用程式程式碼，即可提供強大的篩選、排序及群組功能。  
  
3.  它們只需要一點修改，甚至不用修改，便可以移植到其他資料來源。  
  
 一般而言，越複雜您想要的資料上執行的作業，您會發現使用 LINQ 取代傳統反覆項目技術更多的好處。  
  
 本章節的目的在於示範一些精選的範例的 LINQ 方法。 而不是要提供詳細的說明。  
  
## <a name="in-this-section"></a>本章節內容  
 [LINQ 和字串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 說明如何使用 LINQ，查詢及轉換字串與字串集合。 此外也包含示範這些原理的主題連結。  
  
 [LINQ 和反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 示範如何 LINQ 會使用反映的範例連結。  
  
 [LINQ 和檔案目錄 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 說明如何使用 LINQ 與檔案系統互動。 此外也包含示範這些概念的主題連結。  
  
 [如何︰ 使用 LINQ (Visual Basic) 查詢 ArrayList](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 示範如何以 C# 查詢 ArrayList。  
  
 [如何︰ 新增 LINQ 查詢 (Visual Basic) 的自訂方法](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 說明如何擴充方法，您可以加入的擴充方法使用 LINQ 查詢的集合<xref:System.Collections.Generic.IEnumerable%601>介面。</xref:System.Collections.Generic.IEnumerable%601>  
  
 [語言整合查詢 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 提供主題連結，說明 LINQ，並提供執行查詢的程式碼範例。
