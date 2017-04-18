---
title: "查詢物件的集合"
description: "如何查詢集合。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6694d28355b638c1fe55df0b44700f2dd8d839de
ms.lasthandoff: 03/13/2017

---
# <a name="query-a-collection-of-objects"></a>查詢物件的集合
這個範例示範如何對 `Student` 物件清單執行簡單查詢。 每個 `Student` 物件都包含學生的一些基本資訊，以及一份代表學生四次考試分數的清單。  
  
 這個應用程式作為本節中使用相同 `students` 資料來源的許多其他範例的架構。  
  
## <a name="example"></a>範例  
 下列查詢會傳回第一次考試分數等於或高於 90 的學生。  
  
 [!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 此查詢是刻意簡單，好讓您進行體驗。 例如，您可以在 `where` 子句中嘗試多個條件，或使用 `orderby` 子句來排序結果。  
  

## <a name="see-also"></a>請參閱  
 [LINQ 查詢運算式](index.md)
