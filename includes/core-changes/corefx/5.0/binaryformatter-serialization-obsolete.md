---
ms.openlocfilehash: c5204e8c80cb737338b053c39083c0cc43786447
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517320"
---
### <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a>ASP.NET 應用程式中的 BinaryFormatter 序列化方法已過時且禁止

`Serialize`、和上的和 `Deserialize` 方法 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Runtime.Serialization.Formatter> <xref:System.Runtime.Serialization.IFormatter> 現在已過時。 此外， <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ASP.NET 應用程式預設會禁止序列化。

#### <a name="change-description"></a>變更描述

由於中的[安全性弱點](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ，下列方法現在已過時。 此外，在 ASP.NET 5.0 和更新版本的應用程式中， <xref:System.NotSupportedException> 除非 web 應用程式已重新啟用功能，否則它們會擲回 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 。

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

在 .NET 生態系統中，這些方法會被標示為過時，做為停止使用的一部分 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 。

下列序列化方法現在也已經過時，但沒有任何行為變更：

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 8

#### <a name="recommended-action"></a>建議的動作

- 停止 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 在您的程式碼中使用。 相反地，請考慮使用 <xref:System.Text.Json.JsonSerializer> 或 <xref:System.Xml.Serialization.XmlSerializer> 。 如需詳細資訊，請參閱[BinaryFormatter 安全性指南](../../../../docs/standard/serialization/binaryformatter-security-guide.md)。

- 您可以暫時隱藏 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 編譯時期警告，也就是 `SYSLIB0011` 。 我們建議您在選擇此選項之前，先徹底評估您的程式碼是否有風險。 抑制警告最簡單的方式，就是使用指示詞來括住個別的呼叫位置 `#pragma` 。

  ```csharp
  // Now read the purchase order back from disk
  using (var readStream = new FileStream("myfile.bin", FileMode.Open))
  {
      var formatter = new BinaryFormatter();
  #pragma warning disable SYSLIB0011
      return (PurchaseOrder)formatter.Deserialize(readStream);
  #pragma warning restore SYSLIB0011
  }
  ```

  您也可以在專案檔中隱藏警告。

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  如果您在專案檔中隱藏警告，則會針對專案中的所有程式碼檔案隱藏警告。 隱藏 SYSLIB0011 並不會隱藏使用其他已淘汰的 Api 所造成的警告。

- 若要繼續 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 在 ASP.NET apps 中使用，您可以在專案檔中重新啟用它。 不過，強烈建議不要這麼做。 如需詳細資訊，請參閱[BinaryFormatter 安全性指南](../../../../docs/standard/serialization/binaryformatter-security-guide.md)。

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

如需建議動作的詳細資訊，請參閱[解決 BinaryFormatter obsoletion 和停用錯誤](https://aka.ms/binaryformatter)。

#### <a name="category"></a>類別

- Core .NET 程式庫
- ASP.NET

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
