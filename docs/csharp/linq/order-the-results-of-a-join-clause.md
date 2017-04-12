---
title: "排序 join 子句的結果"
description: "如何排序 join 子句的結果。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0252dd62e5638ffd1ab4eeebcfc2382a65997e30
ms.lasthandoff: 03/13/2017

---
# <a name="order-the-results-of-a-join-clause"></a>排序 join 子句的結果
本例示範如何排序聯結作業的結果。 請注意，排序是在聯結後執行。 雖然您可以在聯結之前使用 `orderby` 子句搭配一或多個來源序列，但通常不建議這麼做。 某些 LINQ 提供者在聯結後可能不會保留排序。  
  
## <a name="example"></a>範例  
 此查詢會建立群組聯結，然後根據類別項目排序仍在範圍內的群組。 在匿名型別初始設定式內，子查詢會排序產品序列中的所有相符項目。  
  
 [!code-cs[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a>請參閱  
 [LINQ 查詢運算式](index.md)   
 [orderby 子句](../language-reference/keywords/orderby-clause.md)   
 [join 子句](../language-reference/keywords/join-clause.md) 
