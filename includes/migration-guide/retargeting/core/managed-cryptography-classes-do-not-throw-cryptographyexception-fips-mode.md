---
ms.openlocfilehash: f1f37e61917e8331b06d91e6abebfe4ce3288e7c
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69564341"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a>受控加密類別在 FIPS 模式中不會擲回 CryptographyException

|   |   |
|---|---|
|詳細資料|在舊版 .NET Framework 4.7.2 及更早版本中，受控加密提供者類別 (例如 <xref:System.Security.Cryptography.SHA256Managed>) 會在系統密碼編譯程式庫以 FIPS 模式設定時擲回 <xref:System.Security.Cryptography.CryptographicException>。 因為受控版本未經過 FIPS (聯邦資訊處理標準) 140-2 認證，並封鎖可能不受 FIPS 規則核准的加密演算法，因此會擲回這些例外狀況。  因為只有極少數開發人員以 FIP 模式使用開發電腦，因此這些例外狀況通常僅在生產系統上擲回。以 .NET Framework 4.8 及更新版本為目標的應用程式，會自動切換至較新且寬鬆的原則，以便不再於此情況下根據預設擲回 <xref:System.Security.Cryptography.CryptographicException>。 相反地，這些受控加密類別會將加密作業重新導向到系統加密程式庫。 此原則變更有效地去除了開發人員環境與生產環境之間的潛在混淆，而且讓原生元件與受控元件在相同的密碼編譯原則下執行。|
|建議|如果不需要此行為，您可以選擇退出並還原先前行為，以便透過將下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 組態設定新增至應用程式組態檔的 [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，在 FIPS 模式中擲回 <xref:System.Security.Cryptography.CryptographicException>：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.UseLegacyFipsThrow=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>如果您的應用程式以 .NET Framework 4.7.2 或更早版本為目標，您也可以透過將下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 組態設定新增至應用程式組態檔的 [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，選擇套用此變更：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.UseLegacyFipsThrow=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.8|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType></li></ul>|
