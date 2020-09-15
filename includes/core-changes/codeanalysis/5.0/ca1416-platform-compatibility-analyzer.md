---
ms.openlocfilehash: e3c9f23ca73ed9b85d09680ec15251ebe02c7f8e
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065140"
---
### <a name="ca1416-platform-compatibility"></a>CA1416：平臺相容性

預設會啟用 .NET 程式碼分析器規則 CA1416，從 .NET 5.0 開始。 它會從未驗證作業系統的呼叫網站，產生對平臺特定 Api 呼叫的組建警告。

#### <a name="change-description"></a>變更描述

從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。 預設會啟用這些規則中的數個，包括 CA1416。 如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。 當您從平臺內容未通過驗證的位置使用平臺特定 Api 時，規則 CA1416 會通知您。

「平臺相容性分析器」規則 CA1416 與 .NET 5.0 的一些新功能搭配使用。 .NET 5.0 引進 `SupportedOSPlatformAttribute` 和 `UnsupportedOSPlatformAttribute` 屬性 (<xref:System.Runtime.Versioning.MinimumOSPlatformAttribute> <xref:System.Runtime.Versioning.RemovedInOSPlatformAttribute> 在先前的預覽版本中) ，可讓您指定不支援 API 的平臺。 *is* *isn't* 如果沒有這些屬性，則會假設所有平臺都支援 API。 這些屬性已套用至核心 .NET 程式庫中的平臺特定 Api。

在以無法使用其所使用之 Api 的平臺為目標的專案中，規則 CA1416 會旗標平臺特定的 API 呼叫，其中不會驗證平臺內容。 大部分現在以和屬性裝飾的 Api，在 `SupportedOSPlatformAttribute` `UnsupportedOSPlatformAttribute` 不受支援的作業系統上叫用時，會擲回 <xref:System.PlatformNotSupportedException> 例外狀況。 既然這些 Api 已標示為平臺特定，規則 CA1416 可協助您藉 <xref:System.PlatformNotSupportedException> 由將作業系統檢查新增至呼叫位置，以防止執行時間例外狀況。

#### <a name="examples"></a>範例

- <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType>只有在 Windows 上才支援此方法， (它是以 `[SupportedOSPlatform("windows")]`) 裝飾。 如果專案的 [目標](../../../../docs/standard/frameworks.md)為 `net5.0` (但未) ，則下列程式碼會在組建階段產生 CA1416 警告 `net5.0-windows` 。 您可以採取的動作來避免警告，請參閱 [建議的動作](#recommended-action)。

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- 在 <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> 瀏覽器中不支援此方法 (它是以 `[UnsupportedOSPlatform("browser")]`) 裝飾。 如果專案使用 Blazor WebAssembly SDK (`<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">`) 或包含 `browser` 在專案檔中) 支援的平臺 (，則下列程式碼會在組建階段產生 CA1416 警告 `<SupportedPlatform Include="browser" />` 。

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

#### <a name="version-introduced"></a>引進的版本

5.0 RC1

#### <a name="recommended-action"></a>建議的動作

確定只有在程式碼在適當的平臺上執行時，才會呼叫平臺特定的 Api。 您可以使用類別中的其中一個方法來檢查目前的作業系統 `Is<Platform>` <xref:System.OperatingSystem?displayProperty=nameWithType> ，例如，在 `System.OperatingSystem.IsWindows()` 呼叫平臺特定 API 之前。

您可以 `Is<Platform>` 在語句的條件中使用其中一個方法 `if` ：

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

或者，如果您不想要在執行時間額外負荷額外的 `if` 語句，請 <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> 改為呼叫：

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

您也可以將 API 標示為平臺特定，在這種情況下，檢查需求的負擔會落在您的呼叫端。 您可以標記特定的方法或類型或整個元件。

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

如果您不想要修正所有的呼叫位置，可以選擇下列其中一個選項來抑制警告：

- 若要隱藏規則 CA1416，您可以使用 `#pragma` 或 [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) 編譯器旗標，或在 editorconfig 檔案中 [將規則的嚴重性設定](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) 為 `none` 。

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- 若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。 如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。

#### <a name="category"></a>類別

- 程式碼分析
- Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

針對 Windows 平臺：

- 所有列出的 Api <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md> 。
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

針對 Blazor WebAssembly platform：

- 所有列出的 Api <https://github.com/dotnet/runtime/issues/41087> 。

<!--

#### Affected APIs

- ``

-->

#### <a name="see-also"></a>另請參閱

- [.NET API 分析器](../../../../docs/standard/analyzers/api-analyzer.md)
