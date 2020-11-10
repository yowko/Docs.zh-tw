---
title: .NET 5 + 中已淘汰的功能
description: 瞭解在 .NET 5.0 和更新版本中標示為過時的 Api，這些 Api 會產生 SYSLIB 編譯器警告。
ms.date: 10/20/2020
ms.openlocfilehash: aa5716ba8fe46c7c4ae2faafe7cc963551eecef7
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440760"
---
# <a name="obsolete-features-in-net-5"></a>.NET 5 中已淘汰的功能

從 .NET 5.0 開始，某些新標記為過時的 Api 會使用上的兩個新屬性 <xref:System.ObsoleteAttribute> 。

- <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType>屬性會指示編譯器使用自訂診斷識別碼產生組建警告。 自訂識別碼可讓您明確地隱藏 obsoletion 警告，以及彼此分開隱藏。 在 .NET 5 + obsoletions 的情況下，自訂診斷識別碼的格式為 `SYSLIBxxxx` 。

- <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType>屬性會指示編譯器包含 URL 連結，以深入瞭解 obsoletion。

如果您因為使用過時的 API 而遇到組建警告或錯誤，請遵循 [參考](#reference) 一節中所列的診斷識別碼所提供的特定指導方針。 針對過時的類型或成員， *無法* 使用 [標準診斷識別碼 (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) 來抑制這些 obsoletions 的警告或錯誤;請改用自訂 `SYSLIBxxxx` 診斷識別碼值。 如需詳細資訊，請參閱 [隱藏警告](#suppress-warnings)。

## <a name="reference"></a>參考

下表提供 `SYSLIBxxxx` .net 5 + 中 obsoletions 的索引。

| 診斷識別碼 | 說明 |
| - | - |
| [SYSLIB0001](syslib0001.md) | UTF-7 編碼並不安全，因此不應該使用。 請考慮改為使用 UTF-8。 |
| [SYSLIB0002](syslib0002.md) | <xref:System.Security.Permissions.PrincipalPermissionAttribute> 執行時間不接受，而且不得使用。 |
| [SYSLIB0003](syslib0003.md) | 執行時間不支援或不接受代碼啟用安全性 (CAS) 。 |
| [SYSLIB0004](syslib0004.md) | 不支援 (CER) 功能的限制執列區域。 |
| [SYSLIB0005](syslib0005.md) | 不支援全域組件快取 (GAC) 。 |
| [SYSLIB0006](syslib0006.md) | <xref:System.Threading.Thread.Abort?displayProperty=nameWithType> 不受支援，而且會擲回 <xref:System.PlatformNotSupportedException> 。 |
| [SYSLIB0007](syslib0007.md) | 不支援此密碼編譯演算法的預設執行。 |
| [SYSLIB0008](syslib0008.md) | <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator>不支援並擲回 API <xref:System.PlatformNotSupportedException> 。 |
| [SYSLIB0009](syslib0009.md) | <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>和 <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> 方法不受支援，而且會擲回 <xref:System.PlatformNotSupportedException> 。 |
| [SYSLIB0010](syslib0010.md) | 某些遠端 Api 不受支援且會擲回 <xref:System.PlatformNotSupportedException> 。 |
| [SYSLIB0011](syslib0011.md) | <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 序列化已過時，不應該使用。 |
| [SYSLIB0012](syslib0012.md) | <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> 和 <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> 只包含 .NET Framework 相容性。 請改用 <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>。 |

## <a name="suppress-warnings"></a>隱藏警告

如果您必須使用已淘汰的 Api，且 `SYSLIBxxxx` 診斷未顯示為錯誤，您可以在程式碼或專案檔中隱藏警告。

在程式碼中：

```csharp
// Disable the warning.
#pragma warning disable SYSLIB0001
// Code that uses obsolete API.
...
// Re-enable the warning.
#pragma warning restore SYSLIB0001
```

專案檔：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
   <TargetFramework>net5.0</TargetFramework>
   <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
   <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
   <!-- To suppress multiple warnings, you can use multiple NoWarn elements -->
   <NoWarn>$(NoWarn);SYSLIB0002</NoWarn>
   <NoWarn>$(NoWarn);SYSLIB0003</NoWarn>
   <!-- Alternatively, you can suppress multiple warnings by using a semicolon-delimited list -->
   <NoWarn>$(NoWarn);SYSLIB0001;SYSLIB0002;SYSLIB0003</NoWarn>
  </PropertyGroup>
</Project>
```

> [!NOTE]
> 以這種方式隱藏警告只會停用您指定的 obsoletion 警告。 它不會停用任何其他警告，包括具有不同診斷識別碼的 obsoletion 警告。
