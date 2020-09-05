---
ms.openlocfilehash: 7f8f97adcca7e66fa5756212bb977daadd92b8b6
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496504"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="d00f5-101">現在，當 .NET 無法處理憑證時，X509Certificate2.ToString(Boolean) 不會擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="d00f5-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

#### <a name="details"></a><span data-ttu-id="d00f5-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d00f5-102">Details</span></span>

<span data-ttu-id="d00f5-103">在 .NET Framework 4.5.2 和更早版本中，如果將 <code>true</code> 傳遞給詳細資訊參數，但 .NET Framework 不支援已安裝的憑證時，此方法會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d00f5-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="d00f5-104">現在，此方法會成功，並傳回省略無法存取之憑證部分的有效字串。</span><span class="sxs-lookup"><span data-stu-id="d00f5-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d00f5-105">建議</span><span class="sxs-lookup"><span data-stu-id="d00f5-105">Suggestion</span></span>

<span data-ttu-id="d00f5-106">您應該更新所有相依於 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> 的程式碼，以確保傳回字串可在 API 先前擲回例外狀況的特定情況下排除某些憑證資料 (例如公開金鑰、私密金鑰和延伸內容)。</span><span class="sxs-lookup"><span data-stu-id="d00f5-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>

| <span data-ttu-id="d00f5-107">名稱</span><span class="sxs-lookup"><span data-stu-id="d00f5-107">Name</span></span>    | <span data-ttu-id="d00f5-108">值</span><span class="sxs-lookup"><span data-stu-id="d00f5-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d00f5-109">範圍</span><span class="sxs-lookup"><span data-stu-id="d00f5-109">Scope</span></span>   |<span data-ttu-id="d00f5-110">Edge</span><span class="sxs-lookup"><span data-stu-id="d00f5-110">Edge</span></span>|
|<span data-ttu-id="d00f5-111">版本</span><span class="sxs-lookup"><span data-stu-id="d00f5-111">Version</span></span>|<span data-ttu-id="d00f5-112">4.6</span><span class="sxs-lookup"><span data-stu-id="d00f5-112">4.6</span></span>|
|<span data-ttu-id="d00f5-113">類型</span><span class="sxs-lookup"><span data-stu-id="d00f5-113">Type</span></span>|<span data-ttu-id="d00f5-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="d00f5-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="d00f5-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d00f5-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)`

-->
