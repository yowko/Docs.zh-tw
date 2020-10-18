---
ms.openlocfilehash: 47c676122df4f0990949a7bfbcd7af8c6144d870
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160529"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a>WinRT 的內建支援已從 .NET 移除

已移除在 .NET 中使用 [Windows 執行時間 (WinRT) ](/uwp/winrt-cref/winrt-type-system) api 的內建支援。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 6

#### <a name="change-description"></a>變更描述

先前，CoreCLR 可以使用 [ (WinMD) 檔案的 Windows 中繼資料](/uwp/winrt-cref/winmd-files) ，並使用 WinRT 類型。 從 .NET 5.0 開始，CoreCLR 無法再直接使用 WinMD 檔案。

如果您嘗試參考不支援的元件，您會收到 <xref:System.IO.FileNotFoundException> 。 如果您啟用 WinRT 類別，您將會收到 <xref:System.PlatformNotSupportedException> 。

這項重大變更的原因如下：

- 因此 WinRT 可以與 .NET 執行時間分開開發和改進。
- 針對其他作業系統（例如 iOS 和 Android）所提供的 interop 系統進行對稱。
- 若要利用其他 .NET 功能，例如 c # 功能、中繼語言 (IL) 連結，以及預先 (的 AOT) 編譯。
- 以簡化 .NET 執行時間程式碼基底。

#### <a name="recommended-action"></a>建議的動作

- 移除對 node.js [封裝](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts)的參考。  相反地，請透過專案的屬性，指定您想要存取的 Windows Api 版本 `TargetFramework` 。  例如：

  ```xml
  <TargetFramework>net5.0-windows10.0.19041</TargetFramework>
  ```

- 使用 [c #/WinRT](/windows/uwp/csharp-winrt/) 工具鏈來產生或自訂 .net 5.0 和更新版本的 WinRT api 和類型。

#### <a name="category"></a>類別

Interop

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

-->
