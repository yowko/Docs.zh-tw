---
ms.openlocfilehash: 1cb6e953aa57c72ee6a2665c521bada10e0786cf
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455780"
---
### <a name="utf-7-code-paths-are-obsolete"></a>UTF-7 程式碼路徑已過時

在應用程式之間已不再使用 UTF-7 編碼，而許多規格現在[禁止其](https://security.stackexchange.com/a/68609/3573)在交換中使用。 它偶爾也會[用來做為](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7)應用程式中的攻擊向量，而不預期會遇到以 utf-7 編碼的資料。 Microsoft 會警告您使用， <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> 因為它不會提供錯誤偵測。

因此， <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 屬性和構造函式 <xref:System.Text.UTF7Encoding.%23ctor%2A> 現在已過時。 此外， <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 和不再 <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> 允許您指定 `UTF-7` 。

#### <a name="change-description"></a>變更描述

之前，您可以使用 api 來建立 UTF-7 編碼的實例 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 。 例如：

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

此外，表示 UTF-7 編碼的實例是由方法所列舉 <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> ，這會列舉 <xref:System.Text.Encoding> 系統上註冊的所有實例。

從 .NET 5.0 開始， <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 屬性和構造函式 <xref:System.Text.UTF7Encoding.%23ctor%2A> 已過時， `SYSLIB0001` (或 `MSLIB0001` 預覽版本) 中產生警告。 不過，若要減少呼叫端在使用類別時所收到的警告數目 <xref:System.Text.UTF7Encoding> ， <xref:System.Text.UTF7Encoding> 類型本身不會標示為已過時。

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

此外，方法會將 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 編碼名稱 `utf-7` 和字碼頁視為 `65000` `unknown` 。 將編碼方式視為 `unknown` 會導致方法擲回 <xref:System.ArgumentException> 。

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

最後， <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> 方法不會在它所傳回的陣列中包含 utf-7 編碼 <xref:System.Text.EncodingInfo> 。 已排除編碼，因為它無法具現化。

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

#### <a name="reason-for-change"></a>變更的原因

許多應用程式 `Encoding.GetEncoding("encoding-name")` 會使用不受信任來源所提供的編碼名稱值來呼叫。 例如，web 用戶端或伺服器可能會取得 `charset` 標頭的部分 `Content-Type` ，並直接將值傳遞給， `Encoding.GetEncoding` 而不進行驗證。 這可能會讓惡意端點指定 `Content-Type: ...; charset=utf-7` ，這可能會導致接收應用程式行為失常。

此外，停用 UTF-7 程式碼路徑，可以優化編譯器（例如 Blazor 所使用的編譯器），以從產生的應用程式中完全移除這些程式碼路徑。 因此，已編譯的應用程式執行效率較高，而且佔用的磁碟空間較少。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 8

#### <a name="recommended-action"></a>建議的動作

在大部分的情況下，您不需要採取任何動作。 不過，如果應用程式先前已啟用與 UTF-7 相關的程式碼路徑，請考慮下列指引。

- 如果您的應用程式 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 使用不受信任的來源所提供的未知編碼名稱進行呼叫：

  相反地，請將編碼名稱與可設定的允許清單進行比較。 可設定的允許清單至少須包含業界標準的 "utf-8"。 視您的用戶端和法規需求而定，您可能也需要允許特定區域的編碼，例如「GB18030」。

  如果您未執行允許清單， <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 將會傳回系統內建的任何， <xref:System.Text.Encoding> 或透過自訂註冊的 <xref:System.Text.EncodingProvider> 。 請審核您的服務需求，以驗證這是否為所需的行為。 除非您的應用程式重新啟用本文章稍後所述的相容性參數，否則，預設會繼續停用 UTF-7。

- 如果您在 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 自己的 <xref:System.Text.UTF7Encoding> 通訊協定或檔案格式中使用或：

  切換至使用 <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> 或 <xref:System.Text.UTF8Encoding> 。 UTF-8 是一種業界標準，在語言、作業系統和執行時間之間廣泛支援。 使用 UTF-8 可簡化程式碼的未來維護，使其更能與生態系統的其餘部分互通。

- 如果您要比較 <xref:System.Text.Encoding> 實例與 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ：

  相反地，請考慮對已知的 UTF-7 字碼頁執行檢查，也就是 `65000` 。 藉由比較字碼頁，您可以避免警告，也會處理一些邊緣案例，例如，如果有人呼叫 `new UTF7Encoding()` 或子類別化型別。

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

- 如果您必須使用 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 或 <xref:System.Text.UTF7Encoding> ：

  您可以 `SYSLIB0001` 在程式碼或專案的 *.csproj*檔案中隱藏警告。

  ```csharp
  #pragma warning disable SYSLIB0001 // Disable the warning.
  Encoding enc = Encoding.UTF7;
  #pragma warning restore SYSLIB0001 // Re-enable the warning.
  ```

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > 隱藏 `SYSLIB0001` 只會停用 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 和 <xref:System.Text.UTF7Encoding> obsoletion 警告。 它不會停用任何其他警告，也不會變更 Api 的行為，例如 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 。

- 如果您必須支援 `Encoding.GetEncoding("utf-7", ...)` ：

  您可以透過相容性參數重新啟用此功能的支援。 此相容性參數可以在應用程式的 *.csproj*檔案或[執行時間設定檔](../../../../docs/core/run-time-config/index.md)中指定，如下列範例所示。

  在應用程式的 *.csproj*檔案中：

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  在應用程式的*runtimeconfig.template.json* file：

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > 如果您重新啟用 UTF-7 的支援，您應該執行呼叫之程式碼的安全性審查 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 。

#### <a name="category"></a>類別

- Core .NET 程式庫
- 安全性

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Encoding.UTF7?displayProperty=fullName>
- <xref:System.Text.UTF7Encoding.%23ctor>
- <xref:System.Text.UTF7Encoding.%23ctor(System.Boolean)>
- <xref:System.Text.Encoding.GetEncoding(System.Int32)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncodings?displayProperty=fullName>

<!--

#### Affected APIs

- `System.Text.Encoding.UTF7`
- `System.Text.UTF7Encoding.#ctor`
- `System.Text.UTF7Encoding.#ctor(System.Boolean)`
- `System.Text.Encoding.GetEncoding(System.Int32)`
- `System.Text.Encoding.GetEncoding(System.String)`
- `System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncodings`

-->
