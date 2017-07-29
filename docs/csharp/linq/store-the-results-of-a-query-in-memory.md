---
title: "將查詢的結果儲存在記憶體中"
description: "如何儲存結果。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 35d908bde06ef55ba2dc93a73211f7be33b9332c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="store-the-results-of-a-query-in-memory"></a>將查詢的結果儲存在記憶體中

查詢基本上是如何擷取和組織資料的一組指令。 要求結果中的每個後續項目時，會延遲執行查詢。 當您使用 `foreach` 逐一查看結果時，會將項目傳回為已存取。 若要評估查詢，並儲存其結果，而不執行 `foreach` 迴圈，則只要在查詢變數上呼叫下列其中一種方法即可︰  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 建議當您儲存查詢結果時，將傳回的集合物件指派給新的變數，如下列範例所示︰  
  
## <a name="example"></a>範例  
 [!code-cs[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a>另請參閱  
 [LINQ 查詢運算式](index.md)

