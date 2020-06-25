---
ms.openlocfilehash: d21b2e092d460fdfc367d0f490228ed44ad5c6cc
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365637"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a>已從 .NET 移除 WinRT 的內建支援

已移除在 .NET 中對[Windows 執行時間（WinRT）](/uwp/winrt-cref/winrt-type-system) api 耗用量的內建支援。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 6

#### <a name="change-description"></a>變更描述

之前，CoreCLR 可能會使用[Windows 中繼資料（WinMD）](/uwp/winrt-cref/winmd-files)檔案進行作用中，並使用 WinRT 類型。 從 .NET 5.0 開始，CoreCLR 不會再直接取用 WinMD 檔案。

如果您嘗試參考不受支援的元件，則會取得 <xref:System.IO.FileNotFoundException> 。 如果您啟用 WinRT 類別，則會取得 <xref:System.PlatformNotSupportedException> 。

這項重大變更的原因如下：

- 因此 WinRT 可以與 .NET 執行時間分開開發和改進。
- 適用于針對其他作業系統（例如 iOS 和 Android）提供之 interop 系統的對稱。
- 若要利用其他 .NET 功能，例如 c # 功能、中繼語言（IL）連結，以及預先進行的（AOT）編譯。
- 以簡化 .NET 執行時間程式碼基底。

#### <a name="recommended-action"></a>建議的動作

- 移除對[Microsoft.Windows.SDK.NET 套件](https://www.nuget.org/packages/microsoft.windows.sdk.net)[的參考，並將](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts)其取代為參考。

- 使用[c #/WinRT](/windows/uwp/csharp-winrt/)工具鏈來產生或自訂 .net 5.0 和更新版本中的 WinRT api 和類型。

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
