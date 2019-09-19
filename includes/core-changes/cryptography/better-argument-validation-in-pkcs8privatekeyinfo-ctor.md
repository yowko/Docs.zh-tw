---
ms.openlocfilehash: f72a9f60d0adcace2df6f1761940f8d8cd33d3af
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119286"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Pkcs8PrivateKeyInfo 的函式中有更好的引數驗證

從 .net Core 3.0 Preview 9 開始，此`Pkcs8PrivateKeyInfo`函式會`algorithmParameters`將參數驗證為單一 BER 編碼的值。 

#### <a name="change-description"></a>變更描述

在 .net Core 3.0 Preview 9 之前，此[ `Pkcs8PrivateKeyInfo`構造](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))函式不`algorithmParameters`會驗證引數。  當這個引數表示不正確值時，此函式會成功，但對任何<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>、 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>、 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>或<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A>方法的呼叫都會擲<xref:System.ArgumentException>回其不接受之引數的（`preEncodedValue`)<xref:System.Security.Cryptography.CryptographicException>或。

如果在 Preview 9 之前以 .net Core 3.0 執行，則只有在呼叫<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>方法時，下列程式碼才會擲回例外狀況：

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

從 .NET Core 3.0 Preview 9 開始，引數會在函式中進行驗證，而不正確值會導致方法<xref:System.Security.Cryptography.CryptographicException>擲回。 這項變更會將例外狀況移到接近資料錯誤的來源。 例如：

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

請確定只提供`algorithmParameters`有效的值，或呼叫`Pkcs8PrivateKeyInfo` <xref:System.ArgumentException>和<xref:System.Security.Cryptography.CryptographicException> （如果需要例外狀況處理時）的函數測試。

### <a name="category"></a>分類

密碼編譯

### <a name="affected-apis"></a>受影響的 API

- [Pkcs8PrivateKeyInfo 的構造函式](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->