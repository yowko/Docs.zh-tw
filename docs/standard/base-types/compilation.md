---
title: "規則運算式中的編譯和重複使用"
description: "規則運算式中的編譯和重複使用"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3adea434-e2ed-4023-b4f5-b0608b4cf53f
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: e14e386a04c64726e4eacb63dc8855a356a18ba0

---

# <a name="compilation-and-reuse-in-regular-expressions"></a>規則運算式中的編譯和重複使用

只要了解規則運算式引擎如何編譯運算式，以及了解如何快取規則運算式，您就可以使大量使用規則運算式的應用程式達到最佳效能。 本主題討論編譯及快取。

## <a name="compiled-regular-expressions"></a>編譯的規則運算式

根據預設，規則運算式引擎會將規則運算式編譯為內部指令的序列 (這些是不同於 Microsoft Intermediate Language (MSIL) 的高階程式碼)。 當引擎執行規則運算式時，它將會解譯內部程式碼。

如果 [Regex](xref:System.Text.RegularExpressions.Regex) 物件是以 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 選項所建構，它會將規則運算式編譯成明確的 MSIL 程式碼，而非高階的規則運算式內部指令。 這允許 .NET 的 Just-in-Time (JIT) 編譯器將運算式轉換為原生機器碼以達到較高效能。

不過，產生的 MSIL 無法卸載。 卸載程式碼的唯一方式就是要卸載整個應用程式定義域 (也就是卸載您應用程式的所有程式碼)。 實際上，以 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 選項編譯規則運算式之後，.NET 絕不會釋放已編譯運算式所使用的資源，即使規則運算式是由 [Regex](xref:System.Text.RegularExpressions.Regex) 物件所建立，而且物件本身被釋放以回收記憶體亦然。

您必須小心限制以 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 選項編譯的不同規則運算式數目，以避免消耗太多資源。 如果應用程式必須使用大量或未限制數目的規則運算式，應該要解譯而不是編譯各個運算式。 不過，如果要重複使用少數規則運算式，應該使用 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 編譯以獲得較高的效能。 

## <a name="the-regular-expressions-cache"></a>規則運算式快取

為了提升效能，規則運算式引擎會維護整個應用程式的已編譯規則運算式之快取。 這個快取會儲存只有在靜態方法呼叫中使用的規則運算式模式 (不會快取提供給執行個體方法的規則運算式模式)。這可避免在每次使用運算式時，必須將其重新剖析為高階位元組程式碼。

快取的規則運算式數目上限取決於 `static` (在 Visual Basic 中為 `Shared`) [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize) 屬性值。 根據預設，規則運算式引擎最多可快取 15 個已編譯的規則運算式。 如果編譯的規則運算式數目超出快取大小，就會捨棄最近最少使用的規則運算式，並快取新的規則運算式。 

您的應用程式可以透過下列其中一種方式，來利用預先編譯的規則運算式：

* 使用 [Regex](xref:System.Text.RegularExpressions.Regex) 物件的靜態方法來定義規則運算式。 如果您使用其他靜態方法呼叫中已定義的規則運算式模式，規則運算式引擎就會從快取中擷取這個規則運算式模式。 如果沒有，則引擎會編譯規則運算式並新增至快取。

* 在需要現有 [Regex](xref:System.Text.RegularExpressions.Regex) 物件的規則運算式模式時重複使用物件。


由於物件具現化和規則運算式編譯會造成額外負荷，因此建立及快速終結多個 [Regex](xref:System.Text.RegularExpressions.Regex) 物件是非常耗費資源的處理序。 對於使用大量不同規則運算式的應用程式，您可以使用靜態 [Regex](xref:System.Text.RegularExpressions.Regex) 方法的呼叫，或增加規則運算式快取的大小，以達到最佳效能。

## <a name="see-also"></a>另請參閱

[.NET 規則運算式](regular-expressions.md)




<!--HONumber=Nov16_HO3-->


