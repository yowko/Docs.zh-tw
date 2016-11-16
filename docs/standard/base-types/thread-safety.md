---
title: "規則運算式中的執行緒安全"
description: "規則運算式中的執行緒安全"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: dc64b681-b3aa-4911-8e30-0764a8b6a852
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 6b410da1982519fd9ff137bd38f1d074ce08d39b

---

# <a name="thread-safety-in-regular-expressions"></a>規則運算式中的執行緒安全

[Regex](xref:System.Text.RegularExpressions.Regex) 類別本身為不變 (唯讀) 的安全執行緒。 也就是說，您可以在任何執行緒上建立 [Regex](xref:System.Text.RegularExpressions.Regex) 物件，並在執行緒之間共用；您也可以從任何執行緒呼叫比對方法，而不會變更任何全域狀態。

不過，[Regex](xref:System.Text.RegularExpressions.Regex) 傳回的結果物件 ([Match](xref:System.Text.RegularExpressions.Match) 和 [MatchCollection)](xref:System.Text.RegularExpressions.MatchCollection) 只可在單一執行緒上使用。 雖然這當中有許多物件在邏輯上是不可變的，但它們的實作可能會延遲某些結果的計算來提升效能，因此，呼叫端必須進行序列化存取。

如果需要在多個執行緒上共用 [Regex](xref:System.Text.RegularExpressions.Regex) 結果物件，可透過呼叫這些物件的同步方法，將其轉換成安全執行緒的執行個體。 所有的規則運算式類別 (除了列舉程式以外) 都是安全執行緒，或可利用同步處理方法轉換為安全執行緒物件。

列舉程式是唯一的例外狀況。 應用程式必須將集合列舉程式的呼叫序列化。 規則是，如果某個集合可以在多個執行緒上同時列舉，您就應該在列舉程式所周遊之集合的根物件位置，同步處理列舉程式方法。

## <a name="see-also"></a>另請參閱

[.NET 規則運算式](regular-expressions.md)




<!--HONumber=Nov16_HO1-->


