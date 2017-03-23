---
title: "如何︰ 使用運算式樹狀架構建置動態查詢 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8d69be78a9f3568535dffe54e21af80c6eb12f70
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>如何︰ 使用運算式樹狀架構建置動態查詢 (Visual Basic)
在 LINQ 中，運算式樹狀架構用來代表結構化的查詢該目標的資料來源實作<xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> 例如，LINQ 提供者會實作<xref:System.Linq.IQueryable%601>介面來查詢關聯式資料存放區。</xref:System.Linq.IQueryable%601> Visual Basic 編譯器會編譯成建置運算式樹狀架構，在執行階段程式碼目標這類資料來源的查詢。 查詢提供者可以周遊的運算式樹狀資料結構，並將它轉譯成適用於資料來源的查詢語言。  
  
 運算式樹狀架構也用於 LINQ 中表示 lambda 運算式指派給變數的型別<xref:System.Linq.Expressions.Expression%601>。</xref:System.Linq.Expressions.Expression%601>  
  
 本主題描述如何建立動態的 LINQ 查詢中使用運算式樹狀架構。 查詢的細節不知道在編譯時期，動態的查詢會很有用。 例如，應用程式可能會提供一個使用者介面，讓使用者指定一或多個述詞來篩選的資料。 若要使用 LINQ 查詢，這類應用程式必須使用運算式樹狀架構，在執行階段建立 LINQ 查詢。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用運算式樹狀架構，來建構查詢`IQueryable`資料來源，然後執行它。 代表下列查詢運算式樹狀架構建置程式碼︰  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 中的 factory 方法<xref:System.Linq.Expressions>命名空間用來建立運算式樹狀架構代表整體查詢所組成的運算式。</xref:System.Linq.Expressions> 代表標準查詢運算子方法呼叫運算式會參考<xref:System.Linq.Queryable>這些方法的實作。</xref:System.Linq.Queryable> 最後一個運算式樹狀結構傳遞給<xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29>的提供者實作`IQueryable`來建立可執行的查詢類型的資料來源`IQueryable`。</xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> 透過列舉查詢變數會取得結果。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 此程式碼會使用固定的數目的運算式中述詞，可傳遞至`Queryable.Where`方法。 不過，您可以撰寫的應用程式，結合多個述詞運算式取決於使用者輸入。 您也可以更改標準查詢運算子在查詢中，根據使用者輸入所呼叫。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   建立新**主控台應用程式**專案。  
  
-   如果沒有參考，加入 system.core.dll 的參考。  
  
-   包括 System.Linq.Expressions 命名空間。  
  
-   複製程式碼範例中，並將它貼到`Main``Sub`程序。  
  
## <a name="see-also"></a>另請參閱  
 [運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)   
 [如何︰ 執行運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
