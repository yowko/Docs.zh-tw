---
title: 規則運算式中的編譯和重複使用
description: 深入瞭解正則運算式中的編譯和重複使用。
ms.topic: conceptual
ms.date: 03/30/2017
helpviewer_keywords:
- parsing text with regular expressions, compilation
- searching with regular expressions, compilation
- .NET regular expressions, engines
- .NET regular expressions, compilation
- regular expressions, compilation
- compilation, regular expressions
- pattern-matching with regular expressions, compilation
- regular expressions, engines
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
ms.openlocfilehash: c834817856d799c5621359a28b8a4c54ea6000d4
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693055"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>規則運算式中的編譯和重複使用

只要了解規則運算式引擎如何編譯運算式，以及了解如何快取規則運算式，您就可以使大量使用規則運算式的應用程式達到最佳效能。 本主題討論編譯及快取。  
  
## <a name="compiled-regular-expressions"></a>編譯的規則運算式  

 根據預設，規則運算式引擎會將規則運算式編譯為內部指令的序列 (這些是不同於 Microsoft Intermediate Language (MSIL) 的高階程式碼)。 當引擎執行規則運算式時，它將會解譯內部程式碼。  
  
 如果 <xref:System.Text.RegularExpressions.Regex> 物件是以 <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> 選項所建構，它會將規則運算式明確地編譯為 MSIL 程式碼，而非高階規則運算式的內部指令。 這允許 .NET 的 Just-in-Time (JIT) 編譯器將運算式轉換為原生機器碼以達到較高效能。  建立物件的成本 <xref:System.Text.RegularExpressions.Regex> 可能較高，但是執行相符專案的成本可能會很小。

 替代方法是使用先行編譯的規則運算式。 您可以使用 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> 方法，將您的所有運算式編譯為一個可重複使用的 DLL。 這可避免在執行時間編譯的需求，但仍可從已編譯的正則運算式速度中獲益。  
  
## <a name="the-regular-expressions-cache"></a>規則運算式快取  

 為了提升效能，規則運算式引擎會維護整個應用程式的已編譯規則運算式之快取。 這個快取會儲存只有在靜態方法呼叫中使用的規則運算式模式 不會快取提供給實例方法 (正則運算式模式。 ) 這可避免在每次使用時，都必須將運算式重新剖析為高階位元組程式碼。  
  
 快取的規則運算式數目上限取決於 `static` (在 Visual Basic 中為 `Shared`) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> 屬性值。 根據預設，規則運算式引擎最多可快取 15 個已編譯的規則運算式。 如果編譯的規則運算式數目超出快取大小，就會捨棄最近最少使用的規則運算式，並快取新的規則運算式。  
  
 您的應用程式可以透過下列兩種方式之一重複使用正則運算式：  
  
- 使用 <xref:System.Text.RegularExpressions.Regex> 物件的靜態方法來定義規則運算式。 如果您使用的正則運算式模式已由另一個靜態方法呼叫定義，則正則運算式引擎會嘗試從快取中取出。 如果快取中未提供，引擎將會編譯正則運算式，並將它新增至快取。
  
- 在需要現有 <xref:System.Text.RegularExpressions.Regex> 物件的規則運算式模式時重複使用該物件。  
  
 由於物件具現化和規則運算式編譯會造成額外負荷，因此建立及快速終結多個 <xref:System.Text.RegularExpressions.Regex> 物件是個非常耗費資源的處理序。 對於使用大量不同規則運算式的應用程式，您可以使用靜態 `Regex` 方法的呼叫，或增加規則運算式快取的大小，以達到最佳效能。  
  
## <a name="see-also"></a>另請參閱

- [.NET 規則運算式](regular-expressions.md)
