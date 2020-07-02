---
ms.openlocfilehash: 0024b2a53444319788b8cdd312d537f994070b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614364"
---
### <a name="sslstream-supports-tls-alerts"></a><span data-ttu-id="bba5a-101">SslStream 支援 TLS 警示</span><span class="sxs-lookup"><span data-stu-id="bba5a-101">SslStream supports TLS Alerts</span></span>

#### <a name="details"></a><span data-ttu-id="bba5a-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bba5a-102">Details</span></span>

<span data-ttu-id="bba5a-103">失敗的 TLS 信號交換之後，第一個 I/O 讀取/寫入作業將會擲回 <xref:System.IO.IOException?displayProperty=fullName> 與內部 <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bba5a-103">After a failed TLS handshake, an <xref:System.IO.IOException?displayProperty=fullName> with an inner <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> exception will be thrown by the first I/O Read/Write operation.</span></span> <span data-ttu-id="bba5a-104">的 <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName> 程式碼 <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> 可以使用[tls 和 SSL 警示的 Schannel 錯誤碼](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts)，從遠端合作物件對應到 tls 警示。如需詳細資訊，請參閱[RFC 2246：區段7.2.2 錯誤警示](https://tools.ietf.org/html/rfc2246#section-7.2.2)。</span><span class="sxs-lookup"><span data-stu-id="bba5a-104">The <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName> code for the <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> can be mapped to the TLS Alert from the remote party using the [Schannel error codes for TLS and SSL alerts](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts).For more information, see [RFC 2246: Section 7.2.2 Error alerts](https://tools.ietf.org/html/rfc2246#section-7.2.2).</span></span> <br/><span data-ttu-id="bba5a-105">.NET Framework 4.6.2 和更早版本的行為是如果另一方交握失敗，傳輸通道 (通常是 TCP 連線) 會在寫入或讀取期間逾時，並在之後立即拒絕連線。</span><span class="sxs-lookup"><span data-stu-id="bba5a-105">The behavior in .NET Framework 4.6.2 and earlier is that the transport channel (usually TCP connection) will timeout during either Write or Read if the other party failed the handshake and immediately afterwards rejected the connection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bba5a-106">建議</span><span class="sxs-lookup"><span data-stu-id="bba5a-106">Suggestion</span></span>

<span data-ttu-id="bba5a-107">呼叫網路 I/O API (例如 <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)>) 的應用程式，應該處理 <xref:System.IO.IOException> 或 <xref:System.TimeoutException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="bba5a-107">Applications calling network I/O APIs such as <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> should handle <xref:System.IO.IOException> or <xref:System.TimeoutException?displayProperty=fullName>.</span></span><br/><span data-ttu-id="bba5a-108">從 .NET Framework 4.7 開始，預設會啟用 TLS 警示功能。</span><span class="sxs-lookup"><span data-stu-id="bba5a-108">The TLS Alerts feature is enabled by default starting with .NET Framework 4.7.</span></span> <span data-ttu-id="bba5a-109">以 .NET Framework 4.0 到 4.6.2 版為目標且在 .NET Framework 4.7 或更高版本的系統上執行的應用程式，會停用此功能以保留相容性。</span><span class="sxs-lookup"><span data-stu-id="bba5a-109">Applications targeting versions of the .NET Framework from 4.0 through 4.6.2 running on a .NET Framework 4.7 or higher system will have the feature disabled to preserve compatibility.</span></span> <br/><span data-ttu-id="bba5a-110">若為在 .NET Framework 4.7 或更新版本上執行之 .NET Framework 4.6 和更新版本的應用程式，您可以使用下列組態 API 來啟用或停用此功能。</span><span class="sxs-lookup"><span data-stu-id="bba5a-110">The following configuration API is available to enable or disable the feature for .NET Framework 4.6 and later applications running on .NET Framework 4.7 or later.</span></span>

- <span data-ttu-id="bba5a-111">以程式設計方式：「必須」是應用程式的第一件事，因為 ServicePointManager 只會初始化一次：</span><span class="sxs-lookup"><span data-stu-id="bba5a-111">Programmatically:   Must be the very first thing the application does since ServicePointManager will initialize only once:</span></span>

    ```csharp
    AppContext.SetSwitch("TestSwitch.LocalAppContext.DisableCaching", true);

    // Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2.
    AppContext.SetSwitch("Switch.System.Net.DontEnableTlsAlerts", true);
    ```

- <span data-ttu-id="bba5a-112">AppConfig：</span><span class="sxs-lookup"><span data-stu-id="bba5a-112">AppConfig:</span></span>

    ```xml
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Net.DontEnableTlsAlerts=true"/>
      <!-- Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2. -->
    </runtime>
    ```

- <span data-ttu-id="bba5a-113">登錄機碼（電腦全域）：將值設定為 `false` ，以啟用 .NET Framework 4.6-4.6.2 中的功能。</span><span class="sxs-lookup"><span data-stu-id="bba5a-113">Registry key (machine global):   Set the Value to `false` to enable the feature in .NET Framework 4.6 - 4.6.2.</span></span>

    ```ini
    Key: HKLM\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts
    - Type: String
    - Value: "true"
    ```

| <span data-ttu-id="bba5a-114">名稱</span><span class="sxs-lookup"><span data-stu-id="bba5a-114">Name</span></span>    | <span data-ttu-id="bba5a-115">值</span><span class="sxs-lookup"><span data-stu-id="bba5a-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bba5a-116">影響範圍</span><span class="sxs-lookup"><span data-stu-id="bba5a-116">Scope</span></span>   | <span data-ttu-id="bba5a-117">Edge</span><span class="sxs-lookup"><span data-stu-id="bba5a-117">Edge</span></span>        |
| <span data-ttu-id="bba5a-118">版本</span><span class="sxs-lookup"><span data-stu-id="bba5a-118">Version</span></span> | <span data-ttu-id="bba5a-119">4.7</span><span class="sxs-lookup"><span data-stu-id="bba5a-119">4.7</span></span>         |
| <span data-ttu-id="bba5a-120">類型</span><span class="sxs-lookup"><span data-stu-id="bba5a-120">Type</span></span>    | <span data-ttu-id="bba5a-121">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="bba5a-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="bba5a-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bba5a-122">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.WebRequest?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Http?displayProperty=nameWithType>
