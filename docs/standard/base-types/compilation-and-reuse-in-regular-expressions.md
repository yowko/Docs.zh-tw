---
title: "規則運算式中的編譯和重複使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework 規則運算式, 編譯"
  - ".NET Framework 規則運算式, 引擎"
  - "編譯, 規則運算式"
  - "使用規則運算式剖析文字, 編譯"
  - "使用規則運算式的模式比對, 編譯"
  - "規則運算式, 編譯"
  - "規則運算式, 引擎"
  - "使用規則運算式搜尋, 編譯"
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 規則運算式中的編譯和重複使用
只要了解規則運算式引擎如何編譯運算式，以及了解如何快取規則運算式，您就可以使大量使用規則運算式的應用程式達到最佳效能。  本主題討論編譯及快取。  
  
## 編譯的規則運算式  
 根據預設，規則運算式引擎會將規則運算式編譯為內部指令的序列 \(Sequence\) \(這些是不同於 Microsoft Intermediate Language \(MSIL\) 的高階程式碼\)。  當引擎執行規則運算式時，它將會解譯內部程式碼。  
  
 如果 <xref:System.Text.RegularExpressions.Regex> 物件是以 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項所建構，它會將規則運算式編譯成明確的 MSIL 程式碼，而非高階的規則運算式內部指令。  這允許 .NET Framework 的 Just\-in\-Time \(JIT\) 編譯器 \(Compiler\) 將運算式轉換為原生機器碼以達到較高效能。  
  
 然而，產生的 MSIL 不能卸載。  卸載程式碼的唯一方式就是要卸載整個應用程式定義域 \(亦即，要卸載您應用程式的全部程式碼\)。  實際上，一旦規則運算式以 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項編譯之後，.NET Framework 絕不會釋放已編譯運算式所使用的資源，即使規則運算式是由 <xref:System.Text.RegularExpressions.Regex> 物件所建立，且物件本身被釋放並被記憶體回收。  
  
 您必須小心限制以 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項編譯的不同規則運算式數目，以避免消耗太多資源。  如果應用程式必須使用大量或未限制數目的規則運算式，應該要解譯而不是編譯各個運算式。  但是，如果要重複使用少數規則運算式，應該使用 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 編譯以獲得較高的效能。  另外一種方式是使用預先編譯好的規則運算式。  您可以使用 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> 方法，將所有運算式編譯成可重複使用的 DLL。  這麼做便不需要在執行階段時進行編譯，而且仍然可以享有已編譯好規則運算式的速度。  
  
## 規則運算式快取  
 為了提升效能，規則運算式引擎維護整個應用程式的已編譯規則運算式之快取。  這個快取會儲存只有在靜態方法呼叫中使用的規則運算式模式 \(不會快取提供給執行個體方法的規則運算式模式\)。這避免在每次使用它時，還要重新剖析運算式為高階位元組程式碼。  
  
 規則運算式的快取上限，是由 `static` \(在 Visual Basic 中為 `Shared`\) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=fullName> 屬性值所決定。  根據預設，規則運算式引擎會快取最多 15 個已編譯的規則運算式。  如果編譯的規則運算式數目超出快取的大小，就會捨棄最近最少使用的規則運算式，並快取新的規則運算式。  
  
> [!IMPORTANT]
>  .NET Framework 2.0 版快取規則運算式的方式與 .NET Framework 1.0 和 1.1 版差異極大。  .NET Framework 1.0 和 1.1 會快取所有的規則運算式，包括靜態方法呼叫和執行個體方法呼叫中所使用的規則運算式。  快取會自動展開以儲存新的規則運算式。  在 .NET Framework 2.0 中，只有靜態方法呼叫中所使用的規則運算式才會快取。  根據預設，會快取最後 15 個規則運算式，但您可以設定 <xref:System.Text.RegularExpressions.Regex.CacheSize%2A> 屬性的值以調整快取的大小。  
  
 您的應用程式可以透過下列其中一種方式，利用預先編譯的規則運算式：  
  
-   使用 <xref:System.Text.RegularExpressions.Regex> 物件的靜態方法，定義規則運算式。  如果您使用其他靜態方法呼叫中已定義的規則運算式模式，規則運算式引擎就會從快取中擷取這個規則運算式模式。  如果沒有，則引擎會編譯規則運算式並新增至快取。  
  
-   重複使用現有的 <xref:System.Text.RegularExpressions.Regex> 物件，只要需要物件的規則運算式模式就可以。  
  
 由於物件具現化及規則運算式編譯的負荷之關係，建立並迅速終結多個 <xref:System.Text.RegularExpressions.Regex> 物件是非常耗費資源的處理序。  對於使用大量不同規則運算式的應用程式，您可以使用靜態 `Regex` 方法的呼叫，或增加規則運算式快取的大小，以達到最佳效能。  
  
## 請參閱  
 [.NET Framework 規則運算式](../../../docs/standard/base-types/regular-expressions.md)