---
title: 重大變更：不支援具現化密碼編譯抽象概念的預設實值
description: '瞭解 .NET 5.0 中的重大變更，在此情況下，密碼編譯抽象概念上的無參數建立 ( # A1 多載已過時。'
ms.date: 10/16/2020
ms.openlocfilehash: 8ed7d0b72347ec41ec65ccd9e4004266619c84f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760740"
---
# <a name="instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported"></a>不支援具現化密碼編譯抽象概念的預設實值

密碼編譯抽象概念上的無參數多載， `Create()` 會因為 .net 5.0 的警告而淘汰。

## <a name="change-description"></a>變更描述

在 .NET Framework 2.0-4.8 中，可以將抽象密碼編譯基本 factory （例如） <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> 設定為傳回不同的演算法。 例如，在預設的 .NET Framework 4.8 安裝上，無參數的靜態方法會傳回 <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> SHA1 演算法的實例，如下列程式碼片段所示。

**僅 .NET Framework**

```csharp
// Return an instance of the default hash algorithm (SHA1).
HashAlgorithm alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA1CryptoServiceProvider'.
Console.WriteLine(alg.GetType());

// Change the default algorithm to be SHA256, not SHA1.
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), typeof(HashAlgorithm).FullName);
alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA256CryptoServiceProvider'.
Console.WriteLine(alg.GetType());
```

您也可以使用 [全電腦](../../../../framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) 設定來變更預設演算法，而不需要以程式設計的 `CryptoConfig` 方式呼叫。

在 .NET Core 2.0-3.1 中，抽象密碼編譯基本 factory，例如 <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> 一律擲回 <xref:System.PlatformNotSupportedException> 。

```csharp
// Throws PlatformNotSupportedException on .NET Core.
HashAlgorithm alg = HashAlgorithm.Create();
```

在 .NET 5.0 和更新版本中，抽象密碼編譯基本處理站（例如） <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> 會標示為已淘汰，並產生識別碼為的編譯時間警告 `SYSLIB0007` 。 在執行時間，這些方法會繼續擲回 <xref:System.PlatformNotSupportedException> 。

```csharp
// Throws PlatformNotSupportedException.
// Also produces compile-time warning SYSLIB0007 on .NET 5+.
HashAlgorithm alg = HashAlgorithm.Create();
```

這是僅限編譯時期的變更。 舊版 .NET Core 沒有任何執行時間變更。

> [!NOTE]
>
> - 只有方法的無參數多載 `Create()` 已過時。 參數化多載尚未過時，且仍如預期般運作。
>
>   ```csharp
>   // Call Create(string), providing an explicit algorithm family name.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   HashAlgorithm hashAlg = HashAlgorithm.Create("SHA256");
>   ```
>
> - *特定* 演算法系列的無參數多載 (不是抽象) 不會過時，且將繼續如預期般運作。
>
>   ```csharp
>   // Call a specific algorithm family's parameterless Create() ctor.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   Aes aesAlg = Aes.Create();
>   ```

## <a name="reason-for-change"></a>變更的原因

.NET Framework 中的密碼編譯設定系統不再存在於 .NET Core 和 .NET 5.0 + 中，因為舊版系統不允許適當的密碼編譯靈活性。 .NET 的回溯相容性需求也會禁止架構更新特定的密碼編譯 Api，以保持密碼編譯的進展。 例如， <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> 當 sha-1 雜湊演算法為最新狀態時，方法就會在 .NET Framework 1.0 中引進。 經過二十年後，現在會將 SHA-1 視為已中斷，但我們無法變更 <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> 來傳回不同的演算法。 這麼做會導致取用應用程式中的不可接受中斷性變更。

最佳做法規定，使用密碼編譯基本類型 (例如 AES、SHA-1 和 RSA) 的程式庫，應能完全掌控它們使用這些基本專案的方式。 需要後續校對的應用程式應該使用更高層級的程式庫，這些程式庫會包裝這些基本專案，並新增金鑰管理和密碼編譯靈活性功能。 裝載環境通常會提供這些程式庫。 其中一個範例是 [ASP。NET 的資料保護程式庫](/aspnet/core/security/data-protection/)，代表呼叫的應用程式處理這些問題。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

- 建議的動作是將對已淘汰 Api 的呼叫取代為特定演算法的 factory 方法呼叫，例如 <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> 。 這可讓您完全掌控要具現化的演算法。

- 如果您需要維持與使用已過時 Api 的 .NET Framework 應用程式所產生之現有承載的相容性，請使用下表中建議的取代。 下表提供從 .NET Framework 預設演算法到其 .NET 5 + 對等專案的對應。

  | .NET Framework | .NET Core/.NET 5.0 + 相容取代 | 備註 |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | SHA-1 演算法會被視為已中斷。 如果可能的話，請考慮使用較強的演算法。 如需進一步指引，請參閱您的安全性顧問。 |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | 大部分新式應用程式不建議採用 HMACSHA1 演算法。 如果可能的話，請考慮使用較強的演算法。 如需進一步指引，請參閱您的安全性顧問。 |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | 大部分新式應用程式不建議採用 HMACSHA1 演算法。 如果可能的話，請考慮使用較強的演算法。 如需進一步指引，請參閱您的安全性顧問。 |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

- 如果您必須繼續呼叫過時的無參數多載 `Create()` ，您可以 `SYSLIB0007` 在程式碼中隱藏警告。

  ```csharp
  #pragma warning disable SYSLIB0007 // Disable the warning.
  HashAlgorithm alg = HashAlgorithm.Create(); // Still throws PNSE.
  #pragma warning restore SYSLIB0007 // Re-enable the warning.
  ```

  您也可以隱藏專案檔中的警告。 這麼做會停用專案內所有原始程式檔的警告。

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0007 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0007</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > 隱藏 `SYSLIB0007` 只會停用此處所列之密碼編譯 api 的 obsoletion 警告。 它不會停用任何其他警告。 此外，即使您隱藏警告，這些過時的 Api 仍然會 <xref:System.PlatformNotSupportedException> 在執行時間擲回。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Security.Cryptography.AsymmetricAlgorithm.Create`
- `M:System.Security.Cryptography.HashAlgorithm.Create`
- `M:System.Security.Cryptography.HMAC.Create`
- `M:System.Security.Cryptography.KeyedHashAlgorithm.Create`
- `M:System.Security.Cryptography.SymmetricAlgorithm.Create`

### Category

- Cryptography

-->
