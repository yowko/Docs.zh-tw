---
ms.openlocfilehash: cf51d5f6b3eee7189fd9613b3d780a829d197a04
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557996"
---
### <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a>在功能上，加密功能僅限初始化

<xref:System.Security.Cryptography.Oid?displayProperty=fullName>用來代表 Asn.1 物件識別碼值和其「易記」名稱的類別，先前是完全可變動的。 這種可變動性經常被忽略，或令人驚訝。 <xref:System.PlatformNotSupportedException>當您嘗試在已指派值之後變更該值時，屬性 setter 現在會擲回。

#### <a name="change-description"></a>變更描述

在先前的版本中，屬性 setter <xref:System.Security.Cryptography.Oid> 可以用來變更 <xref:System.Security.Cryptography.Oid.FriendlyName> 和屬性的值 <xref:System.Security.Cryptography.Oid.Value> 。

在 .NET 5.0 和更新版本中，屬性 setter 只能用來初始化值。 一旦屬性具有值（從函式或先前對屬性 setter 的呼叫），屬性 setter 一律會擲回 <xref:System.PlatformNotSupportedException> 。

#### <a name="reason-for-change"></a>變更的原因

這項變更可讓您在 <xref:System.Security.Cryptography.Oid> 公用 api 中重複使用物件作為傳回值的一部分，以減少物件配置設定檔。 它可避免在將值當做輸入使用時，建立暫時的「防禦」複本 <xref:System.Security.Cryptography.Oid> 。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 8

#### <a name="recommended-action"></a>建議的動作

避免使用 <xref:System.Security.Cryptography.Oid> 屬性 setter （用於物件初始化）。 若要代表新的值，請使用新的實例，而不是變更現有物件的值。

#### <a name="category"></a>類別

密碼編譯

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

-->
