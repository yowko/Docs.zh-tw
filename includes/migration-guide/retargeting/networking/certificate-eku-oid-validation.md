---
ms.openlocfilehash: c996dafcf65b1fd428be908be346de603ead6e0b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615623"
---
### <a name="certificate-eku-oid-validation"></a><span data-ttu-id="9be4b-101">憑證 EKU OID 驗證</span><span class="sxs-lookup"><span data-stu-id="9be4b-101">Certificate EKU OID validation</span></span>

#### <a name="details"></a><span data-ttu-id="9be4b-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9be4b-102">Details</span></span>

<span data-ttu-id="9be4b-103">從 .NET Framework 4.6 開始，<xref:System.Net.Security.SslStream> 或 <xref:System.Net.ServicePointManager> 類別會執行增強金鑰使用方法 (EKU) 物件識別碼 (OID) 驗證。</span><span class="sxs-lookup"><span data-stu-id="9be4b-103">Starting with .NET Framework 4.6, the <xref:System.Net.Security.SslStream> or <xref:System.Net.ServicePointManager> classes perform enhanced key use (EKU) object identifier (OID) validation.</span></span> <span data-ttu-id="9be4b-104">增強金鑰使用方法 (EKU) 延伸模組是表示使用金鑰之應用程式的物件識別碼 (OID) 集合。</span><span class="sxs-lookup"><span data-stu-id="9be4b-104">An enhanced key usage (EKU) extension is a collection of object identifiers (OIDs) that indicate the applications that use the key.</span></span> <span data-ttu-id="9be4b-105">EKU OID 驗證會使用遠端憑證回呼，以確保遠端憑證有用於預定目的的正確 OID。</span><span class="sxs-lookup"><span data-stu-id="9be4b-105">EKU OID validation uses remote certificate callbacks to ensure that the remote certificate has the correct OIDs for the intended purpose.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9be4b-106">建議</span><span class="sxs-lookup"><span data-stu-id="9be4b-106">Suggestion</span></span>

<span data-ttu-id="9be4b-107">如果不需要這項變更，您可以將下列參數新增至 [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 應用程式佈建檔的中的，以停用憑證 EKU OID 驗證：</span><span class="sxs-lookup"><span data-stu-id="9be4b-107">If this change is undesirable, you can disable certificate EKU OID validation by adding the following switch to the [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) in the [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) of your app configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontCheckCertificateEKUs=true" />
</runtime>
```

> [!IMPORTANT]
> <span data-ttu-id="9be4b-108">提供此設定的目的，只是為了回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="9be4b-108">This setting is provided for backward compatibility only.</span></span> <span data-ttu-id="9be4b-109">不建議用於其他用途。</span><span class="sxs-lookup"><span data-stu-id="9be4b-109">Its use is otherwise not recommended.</span></span>

| <span data-ttu-id="9be4b-110">名稱</span><span class="sxs-lookup"><span data-stu-id="9be4b-110">Name</span></span>    | <span data-ttu-id="9be4b-111">值</span><span class="sxs-lookup"><span data-stu-id="9be4b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9be4b-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="9be4b-112">Scope</span></span>   | <span data-ttu-id="9be4b-113">Minor</span><span class="sxs-lookup"><span data-stu-id="9be4b-113">Minor</span></span>       |
| <span data-ttu-id="9be4b-114">版本</span><span class="sxs-lookup"><span data-stu-id="9be4b-114">Version</span></span> | <span data-ttu-id="9be4b-115">4.6</span><span class="sxs-lookup"><span data-stu-id="9be4b-115">4.6</span></span>         |
| <span data-ttu-id="9be4b-116">類型</span><span class="sxs-lookup"><span data-stu-id="9be4b-116">Type</span></span>    | <span data-ttu-id="9be4b-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="9be4b-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="9be4b-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9be4b-118">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
