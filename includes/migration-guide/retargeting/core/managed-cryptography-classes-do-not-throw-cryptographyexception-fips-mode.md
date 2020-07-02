---
ms.openlocfilehash: 0b62eff8d70873293aafa539f40bf032672df57a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617793"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a>受控加密類別在 FIPS 模式中不會擲回 CryptographyException

#### <a name="details"></a>詳細資料

在舊版 .NET Framework 4.7.2 及更早版本中，受控加密提供者類別 (例如 <xref:System.Security.Cryptography.SHA256Managed>) 會在系統密碼編譯程式庫以 FIPS 模式設定時擲回 <xref:System.Security.Cryptography.CryptographicException>。 因為受控版本未經過 FIPS (聯邦資訊處理標準) 140-2 認證，並封鎖可能不受 FIPS 規則核准的加密演算法，因此會擲回這些例外狀況。  因為只有極少數開發人員以 FIP 模式使用開發電腦，因此這些例外狀況通常僅在生產系統上擲回。以 .NET Framework 4.8 及更新版本為目標的應用程式，會自動切換至較新且寬鬆的原則，以便不再於此情況下根據預設擲回 <xref:System.Security.Cryptography.CryptographicException>。 相反地，這些受控加密類別會將加密作業重新導向到系統加密程式庫。 此原則變更有效地去除了開發人員環境與生產環境之間的潛在混淆，而且讓原生元件與受控元件在相同的密碼編譯原則下執行。

#### <a name="suggestion"></a>建議

如果不需要此行為，您可以選擇退出並還原先前行為，以便藉由將下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 組態設定新增至應用程式組態檔的 [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，在 FIPS 模式中擲回 <xref:System.Security.Cryptography.CryptographicException>：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=true" />
</runtime>
```

如果您的應用程式以 .NET Framework 4.7.2 或更早版本為目標，您也可以藉由將下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 組態設定新增至應用程式組態檔的 [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，選擇使用這項變更：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=false" />
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.8         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType>
