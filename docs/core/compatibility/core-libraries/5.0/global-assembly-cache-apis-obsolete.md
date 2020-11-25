---
title: 重大變更：全域組件快取 Api 已淘汰
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中處理 GAC 的 Api 可能會失敗或不執行任何操作。
ms.date: 11/01/2020
ms.openlocfilehash: 2f74fccc68b7a925d909938d77578df8ebe8d60d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760720"
---
# <a name="global-assembly-cache-apis-are-obsolete"></a>全域組件快取 Api 已淘汰

.NET Core 和 .NET 5.0 和更新版本消除了 .NET Framework 中存在的全域組件快取 (GAC) 的概念。 因此，處理 GAC 的所有 .NET Core 和 .NET 5 + Api 都會失敗或不執行任何操作。

為了協助開發人員遠離這些 Api，某些 GAC 相關的 Api 會標示為已淘汰，並 `SYSLIB0005` 在編譯時期產生警告。 這些 Api 可能會在未來的 .NET 版本中移除。

## <a name="change-description"></a>變更描述

下列 Api 已標示為過時。

| API | 標記為過時 |
| - | - |
| <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType> | 5.0 RC1 |

在 .NET Framework 2.x-4.x 中， <xref:System.Reflection.Assembly.GlobalAssemblyCache> `true` 如果查詢的元件是從 GAC 載入，而且 `false` 是從磁片上的其他位置載入，則此屬性會傳回。 在 .NET Core 2.x-3.x 中， <xref:System.Reflection.Assembly.GlobalAssemblyCache> 一律 `false` 會傳回，以反映 GAC 不存在於 .net core 中。

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'True' on .NET Framework, 'False' on .NET Core.
Console.WriteLine(asm.GlobalAssemblyCache);
```

在 .NET 5.0 和更新版本中， <xref:System.Reflection.Assembly.GlobalAssemblyCache> 屬性會繼續一律傳回 `false` 。 不過，屬性 getter 也會標示為已淘汰，以指出呼叫端應該停止存取屬性。 程式庫和應用程式不應使用 <xref:System.Reflection.Assembly.GlobalAssemblyCache> API 來判斷執行時間行為，因為它一律會 `false` 在 .net Core 和 .net 5.0 和更新版本中傳回。

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'False' on .NET 5.0+; also produces warning SYSLIB0005 at compile time.
Console.WriteLine(asm.GlobalAssemblyCache);
```

這是僅限編譯時期的變更。 舊版 .NET Core 沒有任何執行時間變更。

## <a name="reason-for-change"></a>變更的原因

全域組件快取 (GAC) 不會以 .NET Core 和 .NET 5.0 和更新版本的概念存在。

## <a name="version-introduced"></a>引進的版本

.NET 5。0

## <a name="recommended-action"></a>建議的動作

- 如果您的應用程式會查詢 <xref:System.Reflection.Assembly.GlobalAssemblyCache> 屬性，請考慮移除呼叫。 如果您在 <xref:System.Reflection.Assembly.GlobalAssemblyCache> 執行時間使用值來選擇「gac 中的元件」-flow 與「不在 gac 中的元件」的流程，請重新考慮流程對於 .Net Core 或 .net 5.0 + 應用程式是否仍然合理。

- 如果您必須繼續使用已淘汰的 Api，您可以在程式 `SYSLIB0005` 代碼中隱藏警告。

  ```csharp
  Assembly asm = typeof(object).Assembly;
  #pragma warning disable SYSLIB0005 // Disable the warning.
  // Prints 'False' on .NET 5.0+.
  Console.WriteLine(asm.GlobalAssemblyCache);
  #pragma warning restore SYSLIB0005 // Re-enable the warning.
  ```

  您也可以隱藏專案檔中的警告，這會針對專案中的所有原始程式檔停用警告。

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0005 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0005</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  隱藏 `SYSLIB0005` 只會停用 <xref:System.Reflection.Assembly.GlobalAssemblyCache> obsoletion 警告。 它不會停用任何其他警告。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.GlobalAssemblyCache`

-->
