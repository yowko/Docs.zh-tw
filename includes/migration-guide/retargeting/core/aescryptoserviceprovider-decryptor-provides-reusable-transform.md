---
ms.openlocfilehash: 36a9db601f7637185bf48dfcbe2233b4489fcdcf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614329"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>AesCryptoServiceProvider 解密程式提供可重複使用的轉換

#### <a name="details"></a>詳細資料

從以 .NET Framework 4.6.2 為目標的應用程式開始，<xref:System.Security.Cryptography.AesCryptoServiceProvider> 解密程式會提供可重複使用的轉換。 呼叫 <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> 之後，轉換就會重新初始化並且可重複使用。 若為以舊版 .NET Framework 為目標的應用程式，嘗試透過在呼叫 <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> 之後呼叫 <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> 來重複使用解密程式，會擲回 <xref:System.Security.Cryptography.CryptographicException> 或產生損毀的資料。

#### <a name="suggestion"></a>建議

此變更的影響應該很小，因為這是預期的行為。倚賴舊行為的應用程式可以藉由將下列組態設定新增到應用程式設定檔的 `<runtime>` 區段，選擇不使用：

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/>
</runtime>
```

此外，以舊版 .NET Framework 為目標，但是在從 .NET Framework 4.6.2 開始的 .NET Framework 版本下執行的應用程式，可以藉由將下列組態設定新增到應用程式設定檔的 `<runtime>` 區段，來選擇使用：

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/>
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.6.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType>
