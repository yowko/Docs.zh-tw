---
title: 規則運算式中的執行緒安全
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c0bcab0757bc48f6a8216dd5878f0289e49a275
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45617152"
---
# <a name="thread-safety-in-regular-expressions"></a>規則運算式中的執行緒安全
<xref:System.Text.RegularExpressions.Regex> 類別本身為不變 (唯讀) 的安全執行緒。 也就是說，您可以在任何執行緒上建立 **Regex** 物件，並在執行緒之間共用；您也可以從任何執行緒呼叫比對方法，而不會變更任何全域狀態。  
  
 不過，**Regex** 傳回的結果物件 (**Match** 和 **MatchCollection**) 只可在單一執行緒上使用。 雖然這當中有許多物件在邏輯上是不可變的，但它們的實作可能會延遲某些結果的計算來提升效能，因此，呼叫端必須進行序列化存取。  
  
 如果需要在多個執行緒上共用 **Regex** 結果物件，可透過呼叫這些物件的同步方法，將其轉換成安全執行緒的執行個體。 所有的規則運算式類別 (除了列舉程式以外) 都是安全執行緒，或可利用同步處理方法轉換為安全執行緒物件。  
  
 列舉程式是唯一的例外狀況。 應用程式必須將集合列舉程式的呼叫序列化。 規則是，如果某個集合可以在多個執行緒上同時列舉，您就應該在列舉程式所周遊之集合的根物件位置，同步處理列舉程式方法。  
  
## <a name="see-also"></a>另請參閱

- [.NET 規則運算式](../../../docs/standard/base-types/regular-expressions.md)
