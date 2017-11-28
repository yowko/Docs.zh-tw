---
title: "泛型的優點 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], benefits
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f46a328208b49aa33130a020e1a85b6f7aa7d97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="benefits-of-generics-c-programming-guide"></a>泛型的優點 (C# 程式設計手冊)
泛型提供舊版 Common Language Runtime 限制的解決方案，以及透過在通用基底類型 <xref:System.Object> 間來回轉換達成一般化的 C# 語言。 您可以藉由建立泛型類別，在編譯時期建立類型安全的集合。  
  
 您可撰寫簡短的程式，使用 .NET Framework 類別庫的 <xref:System.Collections.ArrayList> 集合類別，示範非泛型集合類別的使用限制。 <xref:System.Collections.ArrayList> 是非常方便的集合類別，不需要修改即可用來儲存任何參考或實值型別。  
  
 [!code-csharp[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_1.cs)]  
  
 但這種便利要付出成本。 任何新增至 <xref:System.Collections.ArrayList> 的參考或實值型別，都會以隱含方式向上轉換成 <xref:System.Object>。 如果項目是實值型別，它們在新增至清單時必須為 boxed，擷取時為 unboxed。 轉換和 boxing 與 unboxing 作業會降低效能。boxing 和 unboxing 在必須重複處理大型集合的案例中，有極其顯著的效果。  
  
 另一個限制是缺乏編譯時期類型檢查，因為 <xref:System.Collections.ArrayList> 會將所有一切轉換成 <xref:System.Object>，在編譯時期，沒有任何方法可以防止用戶端程式碼執行類似這樣的作業：  
  
 [!code-csharp[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_2.cs)]  
  
 雖然完全可以接受且有時是刻意的，但在建立異質集合時，將字串和 `ints` 合併到單一 <xref:System.Collections.ArrayList> 更可能是程式設計錯誤，而且在執行階段之前不會偵測到這個錯誤。  
  
 在 1.0 版和 1.1 版的 C# 語言中，您只能撰寫自己的特定類型集合，避免 .NET Framework 基底類別庫集合類別中的通用程式碼危害。 當然，因為這種類別不能供多個資料類型重複使用，所以沒有一般化的優點，而且必須為要儲存的每個類型重新撰寫類別。  
  
 <xref:System.Collections.ArrayList> 和其他相似類別真正需要的，是能有一種方法，讓用戶端程式碼在每個執行個體上指定它們打算使用的特定資料類型。 這會消除向上轉換成 `T:System.Object` 的需要，也可能會讓編譯器進行類型檢查。 換句話說，<xref:System.Collections.ArrayList> 需要型別參數。 這正是泛型所提供的。 在泛型 <xref:System.Collections.Generic.List%601> 集合的 `N:System.Collections.Generic` 命名空間中，將項目新增至集合的相同作業看起來像這樣：  
  
 [!code-csharp[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_3.cs)]  
  
 對用戶端程式碼而言，相較於 <xref:System.Collections.ArrayList>，唯一以 <xref:System.Collections.Generic.List%601> 新增的語法是宣告和具現化中的型別引數。 以略增加編碼複雜性為代價，您就可以建立比 <xref:System.Collections.ArrayList> 更安全、更快的清單，尤其是當清單項目為實值型別時。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.Generic>  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)  
 [集合最佳做法](http://go.microsoft.com/fwlink/?LinkId=112403)
