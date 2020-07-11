---
ms.openlocfilehash: 207dba9327cfd6debd15c5573697f8950b6c2c95
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86218356"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a><span data-ttu-id="fd749-101">TLS 1.x 依預設會將 SCH_SEND_AUX_RECORD 旗標傳遞至基礎的 SCHANNEL API</span><span class="sxs-lookup"><span data-stu-id="fd749-101">TLS 1.x by default passes the SCH_SEND_AUX_RECORD flag to the underlying SCHANNEL API</span></span>

#### <a name="details"></a><span data-ttu-id="fd749-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fd749-102">Details</span></span>

<span data-ttu-id="fd749-103">使用 TLS 1.x 時，.NET Framework 依賴基礎的 Windows SCHANNEL API。</span><span class="sxs-lookup"><span data-stu-id="fd749-103">When using TLS 1.x, the .NET Framework relies on the underlying Windows SCHANNEL API.</span></span> <span data-ttu-id="fd749-104">從 .NET Framework 4.6 開始，預設會傳遞 [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) 旗標給 SCHANNL。</span><span class="sxs-lookup"><span data-stu-id="fd749-104">Starting with .NET Framework 4.6, the [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) flag is passed by default to SCHANNEL.</span></span> <span data-ttu-id="fd749-105">這會導致 SCHANNEL 分割資料，以便加密成兩個不同的記錄，第一個是單一位元組，第二個則是 <em>n</em>-1 個位元組。在罕見的情況下，這會中斷用戶端與假設資料位於單一記錄中的現有伺服器之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="fd749-105">This causes SCHANNEL to split data to be encrypted into two separate records, the first as a single byte and the second as <em>n</em>-1 bytes.In rare cases, this breaks communication between clients and existing servers that make the assumption that the data resides in a single record.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fd749-106">建議</span><span class="sxs-lookup"><span data-stu-id="fd749-106">Suggestion</span></span>

<span data-ttu-id="fd749-107">如果這項變更會中斷與現有伺服器的通訊，您可以停用傳送 [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) 旗標，並還原先前的行為，不將資料分割成個別的記錄，其方法是新增下列參數到應用程式組態檔 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段中的 [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目：</span><span class="sxs-lookup"><span data-stu-id="fd749-107">If this change breaks communication with an existing server, you can disable sending the [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) flag and restore the previous behavior of not splitting data into separate records by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchSendAuxRecord=true" />
</runtime>
```

> [!IMPORTANT]
> <span data-ttu-id="fd749-108">提供此設定的目的，只是為了回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="fd749-108">This setting is provided for backward compatibility only.</span></span> <span data-ttu-id="fd749-109">不建議用於其他用途。</span><span class="sxs-lookup"><span data-stu-id="fd749-109">Its use is otherwise not recommended.</span></span>

| <span data-ttu-id="fd749-110">名稱</span><span class="sxs-lookup"><span data-stu-id="fd749-110">Name</span></span>    | <span data-ttu-id="fd749-111">值</span><span class="sxs-lookup"><span data-stu-id="fd749-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fd749-112">範圍</span><span class="sxs-lookup"><span data-stu-id="fd749-112">Scope</span></span>   | <span data-ttu-id="fd749-113">Edge</span><span class="sxs-lookup"><span data-stu-id="fd749-113">Edge</span></span>        |
| <span data-ttu-id="fd749-114">版本</span><span class="sxs-lookup"><span data-stu-id="fd749-114">Version</span></span> | <span data-ttu-id="fd749-115">4.6</span><span class="sxs-lookup"><span data-stu-id="fd749-115">4.6</span></span>         |
| <span data-ttu-id="fd749-116">類型</span><span class="sxs-lookup"><span data-stu-id="fd749-116">Type</span></span>    | <span data-ttu-id="fd749-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="fd749-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="fd749-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="fd749-118">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
