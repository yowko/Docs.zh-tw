---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449206"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>在 Pkcs8PrivateKeyInfo 建構函式中更好的參數驗證

從 .NET Core 3.0 預覽`Pkcs8PrivateKeyInfo`9 開始，`algorithmParameters`建構函式將參數驗證為單個 BER 編碼值。

#### <a name="change-description"></a>變更描述

在 .NET Core 3.0 預覽 9 之前，`algorithmParameters`[`Pkcs8PrivateKeyInfo`建構函式](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))未驗證參數。  當此參數表示無效值時，建構函式將成功，但對任何<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>、 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>、 或<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A><xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A>方法的調用將引發他們不接受的參數<xref:System.ArgumentException>的 調用 （`preEncodedValue`） 或 。 <xref:System.Security.Cryptography.CryptographicException>

如果在預覽 9 之前使用 .NET Core 3.0 運行，則以下代碼<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>僅在調用方法時引發異常：

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

從 .NET Core 3.0 預覽 9 開始，在建構函式中驗證參數，無效值會導致方法引發<xref:System.Security.Cryptography.CryptographicException>。 此更改會使異常更接近資料錯誤的來源。 例如：

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 9

#### <a name="recommended-action"></a>建議的動作

確保僅提供有效的`algorithmParameters`值，或者對`Pkcs8PrivateKeyInfo`建構函式測試的調用以及<xref:System.ArgumentException><xref:System.Security.Cryptography.CryptographicException>如果需要異常處理。

### <a name="category"></a>類別

Cryptography

### <a name="affected-apis"></a>受影響的 API

- [Pkcs8私人資訊建構函式](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
