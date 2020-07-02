---
ms.openlocfilehash: ccdf232d743c9e270b6ed21f698998eb95a97399
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621089"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="7ca89-101">WCF MsmqSecureHashAlgorithm 預設值現在是 SHA256</span><span class="sxs-lookup"><span data-stu-id="7ca89-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="7ca89-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7ca89-102">Details</span></span>

<span data-ttu-id="7ca89-103">從 .NET Framework 4.7.1 開始，WCF 中用於 Msmq 訊息的預設訊息簽署演算法是 SHA256。</span><span class="sxs-lookup"><span data-stu-id="7ca89-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="7ca89-104">在 .NET Framework 4.7 和舊版中，預設的訊息簽署演算法是 SHA1。</span><span class="sxs-lookup"><span data-stu-id="7ca89-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7ca89-105">建議</span><span class="sxs-lookup"><span data-stu-id="7ca89-105">Suggestion</span></span>

<span data-ttu-id="7ca89-106">如果在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以在 app.config 檔案的 <code>&lt;runtime&gt;</code> 區段中新增下列程式行來退出變更：</span><span class="sxs-lookup"><span data-stu-id="7ca89-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="7ca89-107">名稱</span><span class="sxs-lookup"><span data-stu-id="7ca89-107">Name</span></span>    | <span data-ttu-id="7ca89-108">值</span><span class="sxs-lookup"><span data-stu-id="7ca89-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7ca89-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="7ca89-109">Scope</span></span>   |<span data-ttu-id="7ca89-110">Minor</span><span class="sxs-lookup"><span data-stu-id="7ca89-110">Minor</span></span>|
|<span data-ttu-id="7ca89-111">版本</span><span class="sxs-lookup"><span data-stu-id="7ca89-111">Version</span></span>|<span data-ttu-id="7ca89-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="7ca89-112">4.7.1</span></span>|
|<span data-ttu-id="7ca89-113">類型</span><span class="sxs-lookup"><span data-stu-id="7ca89-113">Type</span></span>|<span data-ttu-id="7ca89-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="7ca89-114">Runtime</span></span>|
