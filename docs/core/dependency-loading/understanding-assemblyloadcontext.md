---
title: 瞭解 AssemblyLoadCoNtext-.NET Core
description: 瞭解 .NET Core 中 AssemblyLoadCoNtext 之用途和行為的重要概念。
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 293c586163921f9226916b177b3a29cc99c3e695
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70234637"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>瞭解 System.web AssemblyLoadCoNtext

類別<xref:System.Runtime.Loader.AssemblyLoadContext>對於 .net Core 而言是唯一的。 本文會嘗試使用概念資訊<xref:System.Runtime.Loader.AssemblyLoadContext>來補充 API 檔。

這篇文章與執行動態載入的開發人員有關, 特別是動態載入架構開發人員。

## <a name="what-is-the-assemblyloadcontext"></a>什麼是 AssemblyLoadCoNtext？

每個 .NET Core 應用程式都會<xref:System.Runtime.Loader.AssemblyLoadContext>隱含地使用。
這是執行時間的提供者, 用來尋找和載入相依性。 每當載入相依性時, <xref:System.Runtime.Loader.AssemblyLoadContext>就會叫用實例來尋找它。

- 它提供了尋找、載入和快取 managed 元件和其他相依性的服務。

- 為了支援動態程式碼載入和卸載, 它會建立隔離的內容, 以便在自己<xref:System.Runtime.Loader.AssemblyLoadContext>的實例中載入程式碼及其相依性。

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>何時需要多個 AssemblyLoadCoNtext 實例？

單一<xref:System.Runtime.Loader.AssemblyLoadContext>實例限制<xref:System.Reflection.Assembly> 為<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>每個簡單元件名稱只載入一個版本的。

以動態方式載入程式碼模組時, 這種限制可能會造成問題。 每個模組都是獨立編譯的, 而且可能相依于<xref:System.Reflection.Assembly>不同版本的。 當不同的模組相依于常用程式庫的不同版本時, 通常會發生此問題。

為了支援動態載入程式<xref:System.Runtime.Loader.AssemblyLoadContext> <xref:System.Reflection.Assembly>代碼, API 提供在相同的應用程式中載入衝突版本的。 每<xref:System.Runtime.Loader.AssemblyLoadContext>個實例都會提供唯一的字典<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>對應到特定<xref:System.Reflection.Assembly>的實例。

它也提供便利的機制來分組與程式碼模組相關的相依性, 以供稍後卸載。

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>AssemblyLoadCoNtext 實例有何特別意義？

執行時間會在啟動時自動填入實例。<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>  它會使用[預設探查](default-probing.md)來尋找並尋找所有靜態相依性。

它可解決最常見的相依性載入案例。

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>AssemblyLoadCoNtext 如何支援動態相依性？

<xref:System.Runtime.Loader.AssemblyLoadContext>具有可覆寫的各種事件和虛擬函式。

<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>實例僅支援覆寫事件。

「 [Managed 元件載入演算法](loading-managed.md)」、「[附屬元件載入演算法](loading-resources.md)」和「[非受控 (原生) 程式庫載入演算法](loading-unmanaged.md)」文章會參考所有可用的事件和虛擬函式。  這些文章會顯示每個事件和函式在載入演算法中的相對位置。 本文不會重現該資訊。

本節涵蓋相關事件和功能的一般原則。

- **可重複**。 特定相依性的查詢一定會產生相同的回應。 必須傳回相同的已載入相依性實例。 這項需求是快取一致性的基礎。 對於 managed 元件而言, 我們要建立<xref:System.Reflection.Assembly>快取。 快取索引鍵是簡單的元件名稱<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>。
- **通常不會擲**回。  預期當找不到要求的`null`相依性時, 這些函式會傳回而不是擲回。 擲回會提前結束搜尋, 並將例外狀況傳播給呼叫者。 擲回應該限制為非預期的錯誤, 例如元件損毀或記憶體不足的狀況。
- **避免遞迴**。 請注意, 這些函式和處理常式會執行載入規則以尋找相依性。 您的執行不應呼叫觸發遞迴的 Api。 您的程式碼通常應該呼叫需要特定路徑或記憶體參考引數的**AssemblyLoadCoNtext**載入函數。
- **載入正確的 AssemblyLoadCoNtext**。 選擇要載入的相依性是應用程式特有的。  此選項是由這些事件和函式所執行。 當您的程式碼呼叫**AssemblyLoadCoNtext**時, 在您想要載入程式碼的實例上呼叫這些函式。 有時傳回<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>並讓處理負載的工作可能是最簡單的選項。 `null`
- **請留意執行緒爭用**。 載入可由多個執行緒觸發。 AssemblyLoadCoNtext 會藉由將元件自動新增至快取, 來處理執行緒爭用。 會捨棄競爭失敗者的實例。 在您的執行邏輯中, 請勿新增未正確處理多個執行緒的額外邏輯。

## <a name="how-are-dynamic-dependencies-isolated"></a>如何隔離動態相依性？

每<xref:System.Runtime.Loader.AssemblyLoadContext>個實例都代表<xref:System.Reflection.Assembly>實例和<xref:System.Type>定義的唯一範圍。

這些相依性之間沒有二進位隔離。 它們只會被隔離, 而不是依名稱尋找彼此。

在每<xref:System.Runtime.Loader.AssemblyLoadContext>個:

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>可能會參考不同<xref:System.Reflection.Assembly>的實例。
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>可能會針對相同的類型`name`傳回不同的類型實例。

## <a name="how-are-dependencies-shared"></a>如何共用相依性？

您可以輕鬆地在實例<xref:System.Runtime.Loader.AssemblyLoadContext>之間共用相依性。 一般模型是<xref:System.Runtime.Loader.AssemblyLoadContext>用來載入相依性。  另一個則是使用已載入元件的參考來共用相依性。

這是執行時間元件所需的共用。 這些元件只能載入至<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>。 如、或`ASP.NET` `WPF`之類`WinForms`的架構, 這是必要的。

建議您將共用相依性載入至<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>。 這種共用是常見的設計模式。

共用會在自訂<xref:System.Runtime.Loader.AssemblyLoadContext>實例的程式碼中執行。 <xref:System.Runtime.Loader.AssemblyLoadContext>具有可覆寫的各種事件和虛擬函式。 當其中任何函式<xref:System.Reflection.Assembly>傳回在另一個<xref:System.Runtime.Loader.AssemblyLoadContext>實例中載入之實例的參考時, <xref:System.Reflection.Assembly>就會共用實例。 標準負載演算法會延遲以<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>進行載入, 以簡化常見的共用模式。  請參閱[Managed 元件載入演算法](loading-managed.md)。

## <a name="complications"></a>複雜功能

### <a name="type-conversion-issues"></a>類型轉換問題

當兩<xref:System.Runtime.Loader.AssemblyLoadContext>個實例包含具有相同`name`的類型定義時, 它們是不同的類型。 如果和都是來自相同<xref:System.Reflection.Assembly>的實例, 則兩者都是相同的類型。

為了讓事情複雜化, 有關這些不相符類型的例外狀況訊息可能會造成混淆。 在例外狀況訊息中, 這些型別會依照其簡單類型名稱來參考。 在此情況下, 常見的例外狀況訊息的格式如下:

```
Object of type 'IsolatedType' cannot be converted to type 'IsolatedType'.
```

### <a name="debugging-type-conversion-issues"></a>調試型別轉換問題

假設有一對不相符的類型, 也請務必知道:
- 每種類型的<xref:System.Type.Assembly?displayProperty=nameWithType>
- 每個型<xref:System.Runtime.Loader.AssemblyLoadContext>別都可以透過函式取得<xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType> 。

假設有兩`a`個`b`物件和, 則在偵錯工具中評估下列功能將會很有説明:

```C#
// In debugger look at each assembly's instance, Location, and FullName
a.GetType().Assembly
b.GetType().Assembly
// In debugger look at each AssemblyLoadContext's instance and name
System.Runtime.AssemblyLoadContext.GetLoadContext(a.GetType().Assembly)
System.Runtime.AssemblyLoadContext.GetLoadContext(b.GetType().Assembly)
```

### <a name="resolving-type-conversion-issues"></a>解決類型轉換問題

有兩種設計模式可解決這些類型轉換問題。

1. 使用一般共用類型。 這個共用型別可以是基本的執行時間型別, 也可以牽涉到在共用元件中建立新的共用型別。  共用類型通常是在應用程式元件中定義的[介面](../../csharp/language-reference/keywords/interface.md)。 另請參閱：[如何共用](#how-are-dependencies-shared)相依性？。

2. 使用封送處理技術, 從一種類型轉換成另一種。
