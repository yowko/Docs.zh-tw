---
title: "規則運算式中的編譯和重複使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing text with regular expressions, compilation
- searching with regular expressions, compilation
- .NET Framework regular expressions, engines
- .NET Framework regular expressions, compilation
- regular expressions, compilation
- compilation, regular expressions
- pattern-matching with regular expressions, compilation
- regular expressions, engines
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 76acdf2d0d2f7805ec78ea44136bfc63441b9bc9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>規則運算式中的編譯和重複使用
只要了解規則運算式引擎如何編譯運算式，以及了解如何快取規則運算式，您就可以使大量使用規則運算式的應用程式達到最佳效能。 本主題討論編譯及快取。  
  
## <a name="compiled-regular-expressions"></a>編譯的規則運算式  
 根據預設，規則運算式引擎會將規則運算式編譯為內部指令的序列 (這些是不同於 Microsoft Intermediate Language (MSIL) 的高階程式碼)。 當引擎執行規則運算式時，它將會解譯內部程式碼。  
  
 如果<xref:System.Text.RegularExpressions.Regex>物件建構<xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>選項，在編譯規則運算式，以明確的 MSIL 程式碼，而不是高層級的規則運算式內部的指示。 這允許 .NET 的 Just-in-Time (JIT) 編譯器將運算式轉換為原生機器碼以達到較高效能。  
  
不過，產生的 MSIL 無法卸載。 卸載程式碼的唯一方式就是要卸載整個應用程式定義域 (也就是卸載您應用程式的所有程式碼)。 實際上，一旦使用規則運算式編譯<xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>選項，請永遠不會釋放已編譯的運算式所使用的資源，即使由所建立的規則運算式<xref:System.Text.RegularExpressions.Regex>本身釋放回收的物件。  
  
 您必須非常小心限制您使用編譯的規則運算式不同數目<xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>選項，以避免消耗過多資源。 如果應用程式必須使用大量或未限制數目的規則運算式，應該要解譯而不是編譯各個運算式。 不過，如果重複使用少量的規則運算式，它們必須以進行編譯<xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>以提升效能。 替代方法是使用先行編譯的規則運算式。 您可以使用來編譯您的運算式可重複使用的 dll 中的所有<xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A>方法。 這樣可避免在執行階段時仍獲益的速度編譯的規則運算式進行編譯。  
  
## <a name="the-regular-expressions-cache"></a>規則運算式快取  
 為了提升效能，規則運算式引擎會維護整個應用程式的已編譯規則運算式之快取。 這個快取會儲存只有在靜態方法呼叫中使用的規則運算式模式 (不會快取提供給執行個體方法的規則運算式模式)。這可避免在每次使用運算式時，必須將其重新剖析為高階位元組程式碼。  
  
 快取的規則運算式的最大數目取決於值`static`(`Shared`在 Visual Basic 中)<xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType>屬性。 根據預設，規則運算式引擎最多可快取 15 個已編譯的規則運算式。 如果編譯的規則運算式數目超出快取大小，就會捨棄最近最少使用的規則運算式，並快取新的規則運算式。  
  
 您的應用程式可以透過下列其中一種方式，來利用預先編譯的規則運算式：  
  
-   使用的靜態方法<xref:System.Text.RegularExpressions.Regex>來定義規則運算式物件。 如果您使用其他靜態方法呼叫中已定義的規則運算式模式，規則運算式引擎就會從快取中擷取這個規則運算式模式。 如果沒有，則引擎會編譯規則運算式並新增至快取。  
  
-   重複使用現有<xref:System.Text.RegularExpressions.Regex>，只要其規則運算式模式所需的物件。  
  
 因為規則運算式編譯時，建立並快速終結許多物件具現化的負荷，所以<xref:System.Text.RegularExpressions.Regex>物件是非常耗費資源的程序。 對於使用大量的不同的規則運算式的應用程式，您可以藉由呼叫靜態最佳化效能`Regex`方法和可能藉由增加的規則運算式的快取大小。  
  
## <a name="see-also"></a>另請參閱  
 [.NET 規則運算式](../../../docs/standard/base-types/regular-expressions.md)
