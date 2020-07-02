---
ms.openlocfilehash: 0024b2a53444319788b8cdd312d537f994070b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614364"
---
### <a name="sslstream-supports-tls-alerts"></a>SslStream 支援 TLS 警示

#### <a name="details"></a>詳細資料

失敗的 TLS 信號交換之後，第一個 I/O 讀取/寫入作業將會擲回 <xref:System.IO.IOException?displayProperty=fullName> 與內部 <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> 例外狀況。 的 <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName> 程式碼 <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> 可以使用[tls 和 SSL 警示的 Schannel 錯誤碼](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts)，從遠端合作物件對應到 tls 警示。如需詳細資訊，請參閱[RFC 2246：區段7.2.2 錯誤警示](https://tools.ietf.org/html/rfc2246#section-7.2.2)。 <br/>.NET Framework 4.6.2 和更早版本的行為是如果另一方交握失敗，傳輸通道 (通常是 TCP 連線) 會在寫入或讀取期間逾時，並在之後立即拒絕連線。

#### <a name="suggestion"></a>建議

呼叫網路 I/O API (例如 <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)>) 的應用程式，應該處理 <xref:System.IO.IOException> 或 <xref:System.TimeoutException?displayProperty=fullName>。<br/>從 .NET Framework 4.7 開始，預設會啟用 TLS 警示功能。 以 .NET Framework 4.0 到 4.6.2 版為目標且在 .NET Framework 4.7 或更高版本的系統上執行的應用程式，會停用此功能以保留相容性。 <br/>若為在 .NET Framework 4.7 或更新版本上執行之 .NET Framework 4.6 和更新版本的應用程式，您可以使用下列組態 API 來啟用或停用此功能。

- 以程式設計方式：「必須」是應用程式的第一件事，因為 ServicePointManager 只會初始化一次：

    ```csharp
    AppContext.SetSwitch("TestSwitch.LocalAppContext.DisableCaching", true);

    // Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2.
    AppContext.SetSwitch("Switch.System.Net.DontEnableTlsAlerts", true);
    ```

- AppConfig：

    ```xml
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Net.DontEnableTlsAlerts=true"/>
      <!-- Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2. -->
    </runtime>
    ```

- 登錄機碼（電腦全域）：將值設定為 `false` ，以啟用 .NET Framework 4.6-4.6.2 中的功能。

    ```ini
    Key: HKLM\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts
    - Type: String
    - Value: "true"
    ```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.7         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.WebRequest?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Http?displayProperty=nameWithType>
