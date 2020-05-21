---
ms.openlocfilehash: 32030698c12de87daef5e1d8851a0f55ec36d688
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721282"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Pkcs8PrivateKeyInfo 的函式中有更好的引數驗證

從 .NET Core 3.0 Preview 9 開始，此函式會將 `Pkcs8PrivateKeyInfo` `algorithmParameters` 參數驗證為單一 BER 編碼的值。

#### <a name="change-description"></a>變更描述

在 .NET Core 3.0 Preview 9 之前，此[ `Pkcs8PrivateKeyInfo` 構造](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))函式不會驗證 `algorithmParameters` 引數。  當此引數表示不正確值時，此函式會成功，但呼叫 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> 、 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> 、 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A> 或方法的任何 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> 都會擲回 <xref:System.ArgumentException> 其不接受之引數的（ `preEncodedValue` ）或 <xref:System.Security.Cryptography.CryptographicException> 。

如果在 Preview 9 之前以 .NET Core 3.0 執行，則只有在呼叫方法時，下列程式碼才會擲回例外狀況 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> ：

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

從 .NET Core 3.0 Preview 9 開始，引數會在函式中進行驗證，而不正確值會導致方法擲回 <xref:System.Security.Cryptography.CryptographicException> 。 這項變更會將例外狀況移到接近資料錯誤的來源。 例如：

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

請確定只提供有效的 `algorithmParameters` 值，或呼叫 `Pkcs8PrivateKeyInfo` 和（ <xref:System.ArgumentException> <xref:System.Security.Cryptography.CryptographicException> 如果需要例外狀況處理時）的函數測試。

#### <a name="category"></a>類別

密碼編譯

#### <a name="affected-apis"></a>受影響的 API

- [Pkcs8PrivateKeyInfo 的構造函式](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
