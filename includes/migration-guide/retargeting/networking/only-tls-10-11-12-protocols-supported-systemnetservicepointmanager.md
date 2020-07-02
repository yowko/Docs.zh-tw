---
ms.openlocfilehash: 87dc93ece10eaedbfbabddb5f857d0bcd12e05c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615625"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a><span data-ttu-id="8e164-101">在 System.Net.ServicePointManager 和 System.Net.Security.SslStream 只支援 Tls 1.0、1.1 及 1.2 通訊協定</span><span class="sxs-lookup"><span data-stu-id="8e164-101">Only Tls 1.0, 1.1 and 1.2 protocols supported in System.Net.ServicePointManager and System.Net.Security.SslStream</span></span>

#### <a name="details"></a><span data-ttu-id="8e164-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8e164-102">Details</span></span>

<span data-ttu-id="8e164-103">從 .NET Framework 4.6 開始，只有 <xref:System.Net.ServicePointManager> 和 <xref:System.Net.Security.SslStream> 類別可以使用 Tls1.0、Tls1.1 或 Tls 1.2 這三種通訊協定之一。</span><span class="sxs-lookup"><span data-stu-id="8e164-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager> and <xref:System.Net.Security.SslStream> classes are only allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="8e164-104">不支援 SSL3.0 通訊協定與 RC4 編碼器。</span><span class="sxs-lookup"><span data-stu-id="8e164-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8e164-105">建議</span><span class="sxs-lookup"><span data-stu-id="8e164-105">Suggestion</span></span>

<span data-ttu-id="8e164-106">建議的緩和措施是將伺服器端應用程式升級至 Tls1.0、Tls1.1 或 Tls1.2。</span><span class="sxs-lookup"><span data-stu-id="8e164-106">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="8e164-107">如果這並不可行，或是用戶端應用程式已中斷，則可使用 <xref:System.AppContext?displayProperty=fullName> 類別搭配下列兩種方式之一，停用這項功能：</span><span class="sxs-lookup"><span data-stu-id="8e164-107">If this is not feasible, or if client apps are broken, the <xref:System.AppContext?displayProperty=fullName> class can be used to opt out of this feature in either of two ways:</span></span>

- <span data-ttu-id="8e164-108">以程式設計方式設定上的相容性參數 <xref:System.AppContext?displayProperty=fullName> ，如[這裡](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)所述。</span><span class="sxs-lookup"><span data-stu-id="8e164-108">By programmatically setting compat switches on the <xref:System.AppContext?displayProperty=fullName>, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="8e164-109">將下列程式行加入至 app.config 檔案的 `<runtime>` 區段：</span><span class="sxs-lookup"><span data-stu-id="8e164-109">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>
```

| <span data-ttu-id="8e164-110">名稱</span><span class="sxs-lookup"><span data-stu-id="8e164-110">Name</span></span>    | <span data-ttu-id="8e164-111">值</span><span class="sxs-lookup"><span data-stu-id="8e164-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8e164-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="8e164-112">Scope</span></span>   | <span data-ttu-id="8e164-113">Minor</span><span class="sxs-lookup"><span data-stu-id="8e164-113">Minor</span></span>       |
| <span data-ttu-id="8e164-114">版本</span><span class="sxs-lookup"><span data-stu-id="8e164-114">Version</span></span> | <span data-ttu-id="8e164-115">4.6</span><span class="sxs-lookup"><span data-stu-id="8e164-115">4.6</span></span>         |
| <span data-ttu-id="8e164-116">類型</span><span class="sxs-lookup"><span data-stu-id="8e164-116">Type</span></span>    | <span data-ttu-id="8e164-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="8e164-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8e164-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8e164-118">Affected APIs</span></span>

- <xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType>
