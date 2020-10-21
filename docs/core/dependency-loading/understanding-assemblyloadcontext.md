---
title: 瞭解 AssemblyLoadCoNtext-.NET Core
description: 瞭解 .NET Core 中 AssemblyLoadCoNtext 用途和行為的重要概念。
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 4d3f0e50e7c336469bd9af4d1589427388684434
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332818"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>瞭解 AssemblyLoadCoNtext。

<xref:System.Runtime.Loader.AssemblyLoadContext>類別對 .Net Core 而言是唯一的。 本文嘗試以 <xref:System.Runtime.Loader.AssemblyLoadContext> 概念資訊補充 API 檔。

本文與執行動態載入的開發人員相關，尤其是動態載入架構開發人員。

## <a name="what-is-the-assemblyloadcontext"></a>什麼是 AssemblyLoadCoNtext？

每個 .NET Core 應用程式都會隱含地使用 <xref:System.Runtime.Loader.AssemblyLoadContext> 。
它是執行時間的提供者，用來尋找和載入相依性。 當相依性載入時，會叫用 <xref:System.Runtime.Loader.AssemblyLoadContext> 實例以找出它。

- 它提供了尋找、載入及快取 managed 元件和其他相依性的服務。

- 為了支援動態程式碼載入和卸載，它會建立隔離的內容，以在其本身的實例中載入程式碼及其相依性 <xref:System.Runtime.Loader.AssemblyLoadContext> 。

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>何時需要多個 AssemblyLoadCoNtext 實例？

單一 <xref:System.Runtime.Loader.AssemblyLoadContext> 實例限制為 <xref:System.Reflection.Assembly> 每個簡單元件名稱只載入一個版本的 <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> 。

當動態載入程式碼模組時，這種限制可能會變成問題。 每個模組都是獨立編譯的，而且可能相依于不同的版本 <xref:System.Reflection.Assembly> 。 當不同的模組相依于不同版本的常用程式庫時，通常就會發生此問題。

為了支援動態載入程式碼， <xref:System.Runtime.Loader.AssemblyLoadContext> API 可 <xref:System.Reflection.Assembly> 在相同的應用程式中載入的衝突版本。 每個 <xref:System.Runtime.Loader.AssemblyLoadContext> 實例都會提供唯一的字典對應 <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> 至特定的 <xref:System.Reflection.Assembly> 實例。

它也提供便利的機制，以將與程式碼模組相關的相依性分組以供稍後卸載。

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>AssemblyLoadCoNtext 的特殊功能。預設實例是什麼？

<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>執行時間會在啟動時自動填入實例。  它會使用 [預設探查](default-probing.md) 來找出並尋找所有靜態相依性。

它可解決最常見的相依性載入案例。

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>AssemblyLoadCoNtext 如何支援動態相依性？

<xref:System.Runtime.Loader.AssemblyLoadContext> 具有可覆寫的各種事件和虛擬函數。

此 <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> 實例只支援覆寫事件。

[受管理的元件載入演算法](loading-managed.md)、[附屬元件載入演算法](loading-resources.md)和[非受控 (原生) 程式庫載入演算法](loading-unmanaged.md)會參考所有可用的事件和虛擬函式。  這些文章會顯示每個事件和函式在載入演算法中的相對位置。 本文不會重現該資訊。

本節涵蓋相關事件和功能的一般原則。

- **可重複**執行。 特定相依性的查詢一定會產生相同的回應。 必須傳回相同載入的相依性實例。 這項需求是快取一致性的基礎。 尤其是針對 managed 元件，我們會建立快取 <xref:System.Reflection.Assembly> 。 快取索引鍵是簡單的元件名稱 <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> 。
- **通常不會擲**回。  在找不到要求的相依性時，這些函式預期會傳回 `null` 而非擲回。 擲回會提前結束搜尋，並將例外狀況傳播至呼叫端。 擲回應限制為非預期的錯誤，例如元件損毀或記憶體不足的狀況。
- **避免遞迴**。 請注意，這些函式和處理常式會執行用於尋找相依性的載入規則。 您的執行不應呼叫觸發遞迴的 Api。 您的程式碼通常應該呼叫需要特定路徑或記憶體參考引數的 **AssemblyLoadCoNtext** 載入函數。
- **載入至正確的 AssemblyLoadCoNtext**。 選擇載入相依性的位置是應用程式特定的。  此選項是由這些事件和函式所執行。 當您的程式碼呼叫 **AssemblyLoadCoNtext** 時，函式會在您想要載入程式碼的實例上呼叫這些函式。 當您傳回 `null` 並讓 <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> 處理負載的時候，可能是最簡單的選項。
- **請留意執行緒爭用**。 載入可以由多個執行緒觸發。 AssemblyLoadCoNtext 藉由將元件以不可部分完成的方式新增至其快取來處理執行緒爭用。 將會捨棄競爭失敗者的實例。 在您的執行邏輯中，請勿新增未正確處理多個執行緒的額外邏輯。

## <a name="how-are-dynamic-dependencies-isolated"></a>如何隔離動態相依性？

每個 <xref:System.Runtime.Loader.AssemblyLoadContext> 實例都代表 <xref:System.Reflection.Assembly> 實例和定義的唯一範圍 <xref:System.Type> 。

這些相依性之間沒有二進位隔離。 它們只會透過名稱找不到彼此來隔離。

在每個 <xref:System.Runtime.Loader.AssemblyLoadContext> ：

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> 可能參考不同的 <xref:System.Reflection.Assembly> 實例。
- <xref:System.Type.GetType%2A?displayProperty=nameWithType> 可能會針對相同的類型傳回不同的類型實例 `name` 。

## <a name="how-are-dependencies-shared"></a>如何共用相依性？

您可以輕鬆地在實例之間共用相依性 <xref:System.Runtime.Loader.AssemblyLoadContext> 。 一般模型是用來載入相依性的模型 <xref:System.Runtime.Loader.AssemblyLoadContext> 。  另一個則是使用已載入元件的參考來共用相依性。

執行時間元件需要此共用。 這些元件只能載入至 <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> 。 例如、或等架構都需要相同的 `ASP.NET` `WPF` `WinForms` 。

建議將共用的相依性載入至 <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> 。 這種共用是常見的設計模式。

共用會在自訂實例的程式碼中執行 <xref:System.Runtime.Loader.AssemblyLoadContext> 。 <xref:System.Runtime.Loader.AssemblyLoadContext> 具有可覆寫的各種事件和虛擬函數。 當這些函式中有任何一個傳回 <xref:System.Reflection.Assembly> 已載入至另一個實例之實例的參考時 <xref:System.Runtime.Loader.AssemblyLoadContext> ， <xref:System.Reflection.Assembly> 就會共用該實例。 標準載入演算法會延遲 <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> 載入，以簡化常見的共用模式。  請參閱 [Managed 元件載入演算法](loading-managed.md)。

## <a name="complications"></a>複雜功能

### <a name="type-conversion-issues"></a>類型轉換問題

當兩個 <xref:System.Runtime.Loader.AssemblyLoadContext> 實例包含的型別定義相同時 `name` ，就不是相同的類型。 如果只有來自相同的實例，則它們是相同的類型 <xref:System.Reflection.Assembly> 。

為了讓事情變得複雜，這些不相符類型的例外狀況訊息可能會造成混淆。 在例外狀況訊息中，類型是透過其簡單類型名稱來參考。 在此情況下，一般例外狀況訊息的形式如下：

> 類型 ' IsolatedType ' 的物件無法轉換成類型 ' IsolatedType '。

### <a name="debugging-type-conversion-issues"></a>調試型別轉換問題

假設有一組不相符的類型，也請務必瞭解：

- 每個類型的 <xref:System.Type.Assembly?displayProperty=nameWithType>
- 每個型別都 <xref:System.Runtime.Loader.AssemblyLoadContext> 可以透過 <xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType> 函數取得。

假設有兩個物件 `a` 和 `b` ，在偵錯工具中評估下列各項將會很有説明：

```csharp
// In debugger look at each assembly's instance, Location, and FullName
a.GetType().Assembly
b.GetType().Assembly
// In debugger look at each AssemblyLoadContext's instance and name
System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(a.GetType().Assembly)
System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(b.GetType().Assembly)
```

### <a name="resolving-type-conversion-issues"></a>解決類型轉換問題

有兩種設計模式可解決這些類型轉換問題。

1. 使用一般共用類型。 此共用類型可以是基本的執行時間類型，也可以包含在共用元件中建立新的共用類型。  共用類型通常是在應用程式元件中定義的 [介面](../../csharp/language-reference/keywords/interface.md) 。 另請參閱：相依性 [如何共用？](#how-are-dependencies-shared)。

2. 使用封送處理技術，從某個類型轉換成另一個類型。
