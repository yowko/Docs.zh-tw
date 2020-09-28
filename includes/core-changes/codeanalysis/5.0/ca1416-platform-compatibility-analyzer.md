---
ms.openlocfilehash: 4a7616d2ffaabab5279342ebc1082c93a174a52d
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406165"
---
### <a name="ca1416-platform-compatibility"></a>CA1416：平臺相容性

預設會啟用 .NET 程式碼分析器規則 [CA1416](/visualstudio/code-quality/ca1416) ，從 .net 5.0 開始。 它會從未驗證作業系統的呼叫網站，產生對平臺特定 Api 呼叫的組建警告。

#### <a name="change-description"></a>變更描述

從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。 預設會啟用這些規則中的數個，包括 [CA1416](/visualstudio/code-quality/ca1416)。 如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。 當您從平臺內容未通過驗證的位置使用平臺特定 Api 時，規則 CA1416 會通知您。

「平臺相容性分析器」規則 [CA1416](/visualstudio/code-quality/ca1416)與 .net 5.0 的一些新功能搭配使用。 .NET 5.0 引進了 <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 和 <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> ，可讓您指定不支援 API 的平臺*is* 。 *isn't* 如果沒有這些屬性，則會假設所有平臺都支援 API。 這些屬性已套用至核心 .NET 程式庫中的平臺特定 Api。

在以無法使用其所使用之 Api 的平臺為目標的專案中，規則 [CA1416](/visualstudio/code-quality/ca1416) 會旗標平臺特定的 api 呼叫，其中不會驗證平臺內容。 大部分現在以和屬性裝飾的 Api，在 <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> 不受支援的作業系統上叫用時，會擲回 <xref:System.PlatformNotSupportedException> 例外狀況。 既然這些 Api 已標示為平臺特定，規則 [CA1416](/visualstudio/code-quality/ca1416) 可協助您藉 <xref:System.PlatformNotSupportedException> 由將作業系統檢查新增至呼叫位置，以防止執行時間例外狀況。

#### <a name="examples"></a>範例

- <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType>只有在 Windows 上才支援方法，並以裝飾 `[SupportedOSPlatform("windows")]` 。 如果專案的 [目標](../../../../docs/standard/frameworks.md)為 `net5.0` (但未) ，則下列程式碼會在組建階段產生 CA1416 警告 `net5.0-windows` 。 您可以採取的動作來避免警告，請參閱 [建議的動作](#recommended-action)。

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- 在 <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> 瀏覽器中不支援方法，並以裝飾 `[UnsupportedOSPlatform("browser")]` 。 如果專案支援瀏覽器平臺，下列程式碼會在組建階段產生 CA1416 警告。

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

  > [!TIP]
  >
  > - Blazor WebAssembly projects 和 Razor 類別庫專案會自動包含瀏覽器支援。
  > - 若要以手動方式將瀏覽器新增為專案的支援平臺，請將下列專案新增至您的專案檔：
  >
  >  ```xml
  >  <ItemGroup>
  >    <SupportedPlatform Include="browser" />
  >  </ItemGroup>
  >  ```

#### <a name="version-introduced"></a>引進的版本

5.0 RC1

#### <a name="recommended-action"></a>建議的動作

確定只有在程式碼在適當的平臺上執行時，才會呼叫平臺特定的 Api。 您可以使用類別中的其中一個方法來檢查目前的作業系統 `Is<Platform>` <xref:System.OperatingSystem?displayProperty=nameWithType> ，例如，在 <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> 呼叫平臺特定 API 之前。

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

如果您要撰寫程式庫，您可以將 API 標示為平臺特定。 在此情況下，檢查需求的負擔會落在您的呼叫端。 您可以標記特定的方法或類型或整個元件。

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

- [CA1416：驗證平台相容性](/visualstudio/code-quality/ca1416)
- [.NET API 分析器](../../../../docs/standard/analyzers/api-analyzer.md)
