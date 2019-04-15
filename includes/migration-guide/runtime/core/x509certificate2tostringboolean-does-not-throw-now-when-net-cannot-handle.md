---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234164"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="06b79-101">現在，當 .NET 無法處理憑證時，X509Certificate2.ToString(Boolean) 不會擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="06b79-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

|   |   |
|---|---|
|<span data-ttu-id="06b79-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="06b79-102">Details</span></span>|<span data-ttu-id="06b79-103">在 .NET Framework 4.5.2 和更早版本中，如果將 <code>true</code> 傳遞給詳細資訊參數，但 .NET Framework 不支援已安裝的憑證時，此方法會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="06b79-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="06b79-104">現在，此方法會成功，並傳回省略無法存取之憑證部分的有效字串。</span><span class="sxs-lookup"><span data-stu-id="06b79-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>|
|<span data-ttu-id="06b79-105">建議</span><span class="sxs-lookup"><span data-stu-id="06b79-105">Suggestion</span></span>|<span data-ttu-id="06b79-106">您應該更新所有相依於 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> 的程式碼，以確保傳回字串可在 API 先前擲回例外狀況的特定情況下排除某些憑證資料 (例如公開金鑰、私密金鑰和延伸內容)。</span><span class="sxs-lookup"><span data-stu-id="06b79-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>|
|<span data-ttu-id="06b79-107">範圍</span><span class="sxs-lookup"><span data-stu-id="06b79-107">Scope</span></span>|<span data-ttu-id="06b79-108">Edge</span><span class="sxs-lookup"><span data-stu-id="06b79-108">Edge</span></span>|
|<span data-ttu-id="06b79-109">版本</span><span class="sxs-lookup"><span data-stu-id="06b79-109">Version</span></span>|<span data-ttu-id="06b79-110">4.6</span><span class="sxs-lookup"><span data-stu-id="06b79-110">4.6</span></span>|
|<span data-ttu-id="06b79-111">類型</span><span class="sxs-lookup"><span data-stu-id="06b79-111">Type</span></span>|<span data-ttu-id="06b79-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="06b79-112">Runtime</span></span>|
|<span data-ttu-id="06b79-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="06b79-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
