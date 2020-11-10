---
title: SYSLIB0007 警告
description: 瞭解產生編譯時期警告 SYSLIB0007 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 4c0feac1d673e3462a4f2db470825b15cf1b1706
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439935"
---
# <a name="syslib0007-default-implementations-of-cryptography-algorithms-not-supported"></a>SYSLIB0007：不支援密碼編譯演算法的預設執行

.NET Framework 中的密碼編譯配置系統不允許適當的密碼編譯彈性，且不會出現在 .NET Core 和 .NET 5 + 中。 .NET 的回溯相容性需求也會禁止架構更新特定的密碼編譯 Api，以保持密碼編譯的進展。 因此，從 .NET 5.0 開始，會將下列 Api 標記為過時。 使用這些 Api `SYSLIB0007` 時，會在編譯時期產生警告。

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

## <a name="workarounds"></a>因應措施

- 建議的動作是將對已淘汰 Api 的呼叫取代為特定演算法的 factory 方法呼叫，例如 <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> 。 這可讓您完全掌控要具現化的演算法。

- 如果您需要維持與使用已過時 Api 的 .NET Framework 應用程式所產生之現有承載的相容性，請使用下表中建議的取代。 下表提供從 .NET Framework 預設演算法到其 .NET 5 + 對等專案的對應。

  | .NET Framework | .NET Core/.NET 5.0 + 相容取代 | 備註 |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | SHA-1 演算法會被視為已中斷。 如果可能的話，請考慮使用較強的演算法。 如需進一步指引，請參閱您的安全性顧問。 |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | 大部分新式應用程式不建議採用 HMACSHA1 演算法。 如果可能的話，請考慮使用較強的演算法。 如需進一步指引，請參閱您的安全性顧問。 |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | 大部分新式應用程式不建議採用 HMACSHA1 演算法。 如果可能的話，請考慮使用較強的演算法。 如需進一步指引，請參閱您的安全性顧問。 |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>請參閱

- [密碼編譯的重大變更](cryptography.md#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported)
