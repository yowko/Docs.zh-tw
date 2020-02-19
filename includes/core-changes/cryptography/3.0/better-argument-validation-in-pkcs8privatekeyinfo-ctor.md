---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449206"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Pkcs8PrivateKeyInfo 的函式中有更好的引數驗證

從 .NET Core 3.0 Preview 9 開始，`Pkcs8PrivateKeyInfo` 的函式會將 `algorithmParameters` 參數驗證為單一 BER 編碼的值。

#### <a name="change-description"></a>變更描述

在 .NET Core 3.0 Preview 9 之前， [`Pkcs8PrivateKeyInfo`](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))的函式不會驗證 `algorithmParameters` 引數。  當這個引數表示不正確值時，此函式將會成功，但呼叫任何 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>、<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>、<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>或 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> 方法都會擲回不接受的引數 <xref:System.ArgumentException> （`preEncodedValue`）或 <xref:System.Security.Cryptography.CryptographicException>。

如果在 Preview 9 之前以 .NET Core 3.0 執行，下列程式碼只會在呼叫 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> 方法時擲回例外狀況：

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

從 .NET Core 3.0 Preview 9 開始，引數會在函式中進行驗證，而不正確值會導致方法擲回 <xref:System.Security.Cryptography.CryptographicException>。 這項變更會將例外狀況移到接近資料錯誤的來源。 例如：

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

請確定只提供有效的 `algorithmParameters` 值，或如果需要例外狀況處理，則呼叫 `Pkcs8PrivateKeyInfo` 的 <xref:System.ArgumentException> 和 <xref:System.Security.Cryptography.CryptographicException> 測試。

### <a name="category"></a>類別

Cryptography

### <a name="affected-apis"></a>受影響的 API

- [Pkcs8PrivateKeyInfo 的構造函式](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
