---
title: 瞭解程式集載入中文 - .NET 核心
description: 瞭解 .NET Core 中程式集 LoadContext 的目的和行為的關鍵概念。
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 43fb0d792ddeb20b8a141af452a86dd50f37ba43
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523605"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>瞭解系統.執行時.載入程式.程式集載入上下文

類<xref:System.Runtime.Loader.AssemblyLoadContext>對 .NET Core 是唯一的。 本文嘗試用概念資訊<xref:System.Runtime.Loader.AssemblyLoadContext>補充 API 文檔。

本文與實現動態載入的開發人員相關,尤其是動態載入框架開發人員。

## <a name="what-is-the-assemblyloadcontext"></a>什麼是程式集載入上下文?

每個 .NET 核心<xref:System.Runtime.Loader.AssemblyLoadContext>應用程式隱 用使用 。
它是用於查找和載入依賴項的運行時提供程式。 每當載入依賴項時,都會<xref:System.Runtime.Loader.AssemblyLoadContext>調用實例來查找它。

- 它提供定位、載入和緩存託管程式集和其他依賴項的服務。

- 為了支援動態代碼載入和卸載,它為在其自己的<xref:System.Runtime.Loader.AssemblyLoadContext>實例中載入代碼及其依賴項創建了一個隔離上下文。

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>何時需要多個程式集載入上下文實例?

單一<xref:System.Runtime.Loader.AssemblyLoadContext>個 實體僅限於僅載入每個簡單程式集名稱的版本<xref:System.Reflection.Assembly><xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>。

動態載入代碼模組時,此限制可能會成為問題。 每個模組都是獨立編譯的,可能依賴於不同的<xref:System.Reflection.Assembly>版本。 當不同的模組依賴於常用庫的不同版本時,通常會出現此問題。

為了支援動態載入代碼,API<xref:System.Runtime.Loader.AssemblyLoadContext>提供在同一應用程式中載入 衝突<xref:System.Reflection.Assembly>版本的 。 每個<xref:System.Runtime.Loader.AssemblyLoadContext>實體都提供唯一<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>的字典,<xref:System.Reflection.Assembly>將每個實體映射到一個特定實體。

它還提供了一種方便的機制,用於分組與代碼模組相關的依賴項,以便以後卸載。

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>程式集載入上下文.預設實例有哪些特別內容?

<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>實例由啟動時運行時自動填充。  它使用[默認探測](default-probing.md)來查找和查找所有靜態依賴項。

它解決了最常見的依賴項載入方案。

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>程式集載入上下文如何支援動態依賴項?

<xref:System.Runtime.Loader.AssemblyLoadContext>具有可以重寫的各種事件和虛擬函數。

實例<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>僅支援重寫事件。

文章[託管程式集載入演演算法](loading-managed.md)、[附屬程式集載入演演演算法](loading-resources.md)和非[託管(本機)庫載入演演演算法](loading-unmanaged.md)是指所有可用的事件和虛擬函數。  這些文章顯示了每個事件和函數在載入演演演算法中的相對位置。 本文不會重現該資訊。

本節介紹相關事件和職能的一般原則。

- **可重複**。 對特定依賴項的查詢必須始終產生相同的回應。 必須返回相同的載入的依賴項實例。 此要求對於緩存一致性至關重要。 對於託管程式集,我們建立了快取<xref:System.Reflection.Assembly>。 快取鍵是一個簡單的程式集名稱<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>。
- **通常不扔**。  當找不到請求的依賴項時,預計`null`這些函數返回而不是引發。 引發將過早結束搜索,並將異常傳播到調用方。 投擲應限於意外錯誤,如損壞的程式集或記憶體不足條件。
- **避免遞迴**。 請注意,這些函數和處理程式實現了用於查找依賴項的載入規則。 您的實現不應調用觸發遞歸的 API。 代碼通常應呼叫需要特定路徑或記憶體引用參數的**AssemblyLoadContext**載入函數。
- **載入正確的程式集載入中文**。 選擇載入依賴項的位置是特定於應用程式的。  選擇由這些事件和函數實現。 當代碼調用**AssemblyLoadContext**逐路徑載入函數時,在您希望載入代碼的實例上調用它們。 某個時候返回`null`並<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>讓句柄載入可能是最簡單的選項。
- **注意線程爭用**。 載入可以由多個線程觸發。 AssemblyLoadContext 通過原子方式將程式集添加到其緩存來處理線程爭用。 種族失敗者的實例被丟棄。 在實現邏輯中,不要添加無法正確處理多個線程的額外邏輯。

## <a name="how-are-dynamic-dependencies-isolated"></a>如何隔離動態依賴關係?

每個<xref:System.Runtime.Loader.AssemblyLoadContext>實例<xref:System.Reflection.Assembly>表示 實<xref:System.Type>例和 定義的唯一範圍。

這些依賴項之間沒有二進制隔離。 他們只是通過沒有按名字找到對方而孤立。

每個每個<xref:System.Runtime.Loader.AssemblyLoadContext>:

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>可以引用其他<xref:System.Reflection.Assembly>實例。
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>可能為同一類型`name`返回不同類型的實例。

## <a name="how-are-dependencies-shared"></a>如何共用依賴項?

依賴項可以很容易地在實例之間<xref:System.Runtime.Loader.AssemblyLoadContext>共用。 一般模型是一個<xref:System.Runtime.Loader.AssemblyLoadContext>載入依賴項。  另一個通過使用對載入的程式集的引用共享依賴項。

運行時程式集需要此共用。 這些程式集只能載入中<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>。 對於框架(如`ASP.NET``WPF`、`WinForms`或 )也是如此。

建議將共享依賴項載入到<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>中。 此共用是常見的設計模式。

共用在自定義<xref:System.Runtime.Loader.AssemblyLoadContext>實例的編碼中實現。 <xref:System.Runtime.Loader.AssemblyLoadContext>具有可以重寫的各種事件和虛擬函數。 當這些函數中的任何一個返回對在另一<xref:System.Reflection.Assembly><xref:System.Runtime.Loader.AssemblyLoadContext>個 實例中載入的實例的<xref:System.Reflection.Assembly>引用時 ,該實例將共用。 標準負載演演演<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>算法順從 載入以簡化公共共用模式。  請參考[託管程式集載入演算法](loading-managed.md)。

## <a name="complications"></a>複雜功能

### <a name="type-conversion-issues"></a>類型轉換問題

當兩<xref:System.Runtime.Loader.AssemblyLoadContext>個實例包含具有`name`相同 的類型定義時,它們不是同一類型。 它們是同一類型,只有當它們來自同一<xref:System.Reflection.Assembly>個實例時。

使問題複雜化的是,有關這些不匹配類型的異常消息可能會令人困惑。 這些類型在異常消息中由其簡單類型名稱引用。 在這種情況下,常見的異常消息是這樣的形式:

> 類型"隔離類型"的物件不能轉換為類型"隔離類型"。

### <a name="debugging-type-conversion-issues"></a>除錯型態轉換問題

給定一對不匹配的類型,還必須瞭解:

- 每種型別<xref:System.Type.Assembly?displayProperty=nameWithType>
- 每個類型的<xref:System.Runtime.Loader.AssemblyLoadContext>,可通過 函<xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType>數 獲得。

給定兩個`a``b`物件 和 ,在調試器中評估以下內容將很有説明:

```csharp
// In debugger look at each assembly's instance, Location, and FullName
a.GetType().Assembly
b.GetType().Assembly
// In debugger look at each AssemblyLoadContext's instance and name
System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(a.GetType().Assembly)
System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(b.GetType().Assembly)
```

### <a name="resolving-type-conversion-issues"></a>解決類型轉換問題

有兩種設計模式可用於解決這些類型的轉換問題。

1. 使用公共共享類型。 此共享類型可以是基元運行時類型,也可以涉及在共用程式集中創建新的共享類型。  通常,共用類型是在應用程式程式集中定義的[介面](../../csharp/language-reference/keywords/interface.md)。 另請參閱:[如何共享依賴項?](#how-are-dependencies-shared)

2. 使用封送技術從一種類型轉換為另一種類型。
