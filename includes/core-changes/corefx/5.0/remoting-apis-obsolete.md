---
ms.openlocfilehash: 35041a035041fd4ad5402e1bc0dd137a74d4f949
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434942"
---
### <a name="remoting-apis-are-obsolete"></a>遠端 Api 已淘汰

某些遠端相關的 Api 會標示為已淘汰，並 `SYSLIB0010` 在編譯時期產生警告。 這些 Api 可能會在未來的 .NET 版本中移除。

#### <a name="change-description"></a>變更描述

下列遠端 Api 已標示為過時。

| API | 標記為過時 |
| - | - |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | 5.0 RC1 |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | 5.0 RC1 |

在 .NET Framework 2.x-4.x 中， <xref:System.MarshalByRefObject.GetLifetimeService> 和 <xref:System.MarshalByRefObject.InitializeLifetimeService> 方法會控制與 .net 遠端處理相關之實例的存留期。 在 .NET Core 2.x-3.x 中，這些方法一律會 <xref:System.PlatformNotSupportedException> 在執行時間擲回。

在 .NET 5.0 和更新版本中， <xref:System.MarshalByRefObject.GetLifetimeService> 和 <xref:System.MarshalByRefObject.InitializeLifetimeService> 方法會標示為「已淘汰」為「警告」，但會 <xref:System.PlatformNotSupportedException> 在執行時間繼續擲回。

```csharp
// MemoryStream, like all Stream instances, subclasses MarshalByRefObject.
MemoryStream stream = new MemoryStream();
// Throws PlatformNotSupportedException; also produces warning SYSLIB0010.
obj.InitializeLifetimeService();
```

這是僅限編譯時期的變更。 舊版 .NET Core 沒有任何執行時間變更。

#### <a name="reason-for-change"></a>變更的原因

[.Net 遠端處理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) 是一種舊版技術。 它可讓您在另一個進程中具現化物件 (可能甚至在不同的電腦上) 並與該物件互動，就像是一般的同進程 .NET 物件實例一樣。 .NET 遠端基礎結構只存在於 .NET Framework 2.x. x 中。 .NET Core 和 .NET 5.0 和更新版本不支援 .NET 遠端處理，而遠端 Api 不存在或一律在這些執行時間擲回例外狀況。

為了協助開發人員遠離這些 Api，我們會 obsoleting 選取的遠端處理相關 Api。 這些 Api 可能會在未來的 .NET 版本中完全移除。

#### <a name="version-introduced"></a>引進的版本

.NET 5。0

#### <a name="recommended-action"></a>建議的動作

- 請考慮使用以 WCF 或 HTTP 為基礎的 REST 服務，與其他應用程式或電腦之間的物件進行通訊。 如需詳細資訊，請參閱 [.NET FRAMEWORK .Net Core 上無法使用的技術](../../../../docs/core/porting/net-framework-tech-unavailable.md)。

- 如果您必須繼續使用已淘汰的 Api，您可以在程式 `SYSLIB0010` 代碼中隱藏警告。

  ```csharp
  MarshalByRefObject obj = GetMarshalByRefObj();
  #pragma warning disable SYSLIB0010 // Disable the warning.
  obj.InitializeLifetimeService(); // Still throws PNSE.
  obj.GetLifetimeService(); // Still throws PNSE.
  #pragma warning restore SYSLIB0010 // Reenable the warning.
  ```

  您也可以隱藏專案檔中的警告，這會針對專案中的所有原始程式檔停用警告。

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0010 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0010</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  隱藏 `SYSLIB0010` 只會停用遠端 API obsoletion 警告。 它不會停用任何其他警告。 此外，它也不會變更永遠擲回的硬式編碼執行時間行為 <xref:System.PlatformNotSupportedException> 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=fullName>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.MarshalByRefObject.GetLifetimeService`
- `M:System.MarshalByRefObject.InitializeLifetimeService`

-->
