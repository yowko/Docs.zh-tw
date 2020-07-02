---
ms.openlocfilehash: c996dafcf65b1fd428be908be346de603ead6e0b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615623"
---
### <a name="certificate-eku-oid-validation"></a>憑證 EKU OID 驗證

#### <a name="details"></a>詳細資料

從 .NET Framework 4.6 開始，<xref:System.Net.Security.SslStream> 或 <xref:System.Net.ServicePointManager> 類別會執行增強金鑰使用方法 (EKU) 物件識別碼 (OID) 驗證。 增強金鑰使用方法 (EKU) 延伸模組是表示使用金鑰之應用程式的物件識別碼 (OID) 集合。 EKU OID 驗證會使用遠端憑證回呼，以確保遠端憑證有用於預定目的的正確 OID。

#### <a name="suggestion"></a>建議

如果不需要這項變更，您可以將下列參數新增至 [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 應用程式佈建檔的中的，以停用憑證 EKU OID 驗證：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontCheckCertificateEKUs=true" />
</runtime>
```

> [!IMPORTANT]
> 提供此設定的目的，只是為了回溯相容性。 不建議用於其他用途。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.6         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
