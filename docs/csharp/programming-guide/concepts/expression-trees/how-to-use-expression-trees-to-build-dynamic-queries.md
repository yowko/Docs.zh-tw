---
title: "如何：使用運算式樹狀架構建立動態查詢 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7de999848870de80996f308affde088088e32e52
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>如何：使用運算式樹狀架構建立動態查詢 (C#)
在 LINQ 中，您可以使用運算式樹狀架構，來代表以實作 <xref:System.Linq.IQueryable%601> 的資料來源為目標的結構化查詢。 例如，LINQ 提供者會實作 <xref:System.Linq.IQueryable%601> 介面，來查詢關聯式資料存放區。 C# 編譯器會將以這類資料來源為目標的查詢編譯為程式碼，以在執行階段建立運算式樹狀架構。 查詢提供者可接著周遊運算式樹狀架構資料結構，並將它轉譯成適用於資料來源的查詢語言。  
  
 您也可以在 LINQ 中使用運算式樹狀架構，來代表指派給 <xref:System.Linq.Expressions.Expression%601> 類型變數的 Lambda 運算式。  
  
 本主題描述如何使用運算式樹狀架構建立動態 LINQ 查詢。 如果在編譯時不知道查詢的詳細資料，動態查詢會很有用。 例如，應用程式可能會提供一個使用者介面，讓終端使用者指定一或多個述詞來篩選資料。 若要使用 LINQ 進行查詢，這類應用程式必須使用運算式樹狀架構在執行階段建立 LINQ 查詢。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用運算式樹狀架構，對 `IQueryable` 資料來源建構並接著執行查詢。 程式碼會建立運算式樹狀架構來代表下列查詢：  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 <xref:System.Linq.Expressions> 命名空間中的 Factory 方法可用於建立運算式樹狀架構，來代表組成整體查詢的運算式。 代表標準查詢運算子方法呼叫的運算式會參考這些方法的 <xref:System.Linq.Queryable> 實作。 最後一個運算式樹狀架構會傳遞至 `IQueryable` 資料來源的 <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> 實作，以建立 `IQueryable` 類型的可執行檔查詢。 藉由列舉查詢變數可取得結果。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 此程式碼在傳遞至 `Queryable.Where` 方法的述詞中，使用固定數目的運算式。 不過，您可以撰寫一個應用程式，以根據使用者輸入合併可變數目的述詞運算式。 您也可以根據使用者輸入，更改查詢中所呼叫的標準查詢運算子。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   建立新的**主控台應用程式**專案。  
  
-   如果 System.Core.dll 的參考原本未參考，請新增這項參考。  
  
-   加入 System.Linq.Expressions 命名空間。  
  
-   將範例中的程式碼複製並貼到 `Main` 方法中。  
  
## <a name="see-also"></a>另請參閱  
 [運算式樹狀架構 (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)   
 [如何：執行運算式樹狀架構 (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)   
 [如何：在執行階段動態指定述詞篩選](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
