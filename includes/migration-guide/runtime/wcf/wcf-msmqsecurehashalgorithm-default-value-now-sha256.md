---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803545"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="d8dba-101">WCF MsmqSecureHashAlgorithm 預設值現在是 SHA256</span><span class="sxs-lookup"><span data-stu-id="d8dba-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d8dba-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d8dba-102">Details</span></span>|<span data-ttu-id="d8dba-103">從 .NET Framework 4.7.1 開始，WCF 中用於 Msmq 訊息的預設訊息簽署演算法是 SHA256。</span><span class="sxs-lookup"><span data-stu-id="d8dba-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="d8dba-104">在 .NET Framework 4.7 和舊版中，預設的訊息簽署演算法是 SHA1。</span><span class="sxs-lookup"><span data-stu-id="d8dba-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="d8dba-105">建議</span><span class="sxs-lookup"><span data-stu-id="d8dba-105">Suggestion</span></span>|<span data-ttu-id="d8dba-106">如果在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以在 app.config 檔案的 <code>&lt;runtime&gt;</code> 區段中新增下列程式行來退出變更：</span><span class="sxs-lookup"><span data-stu-id="d8dba-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="d8dba-107">範圍</span><span class="sxs-lookup"><span data-stu-id="d8dba-107">Scope</span></span>|<span data-ttu-id="d8dba-108">次要</span><span class="sxs-lookup"><span data-stu-id="d8dba-108">Minor</span></span>|
|<span data-ttu-id="d8dba-109">版本</span><span class="sxs-lookup"><span data-stu-id="d8dba-109">Version</span></span>|<span data-ttu-id="d8dba-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="d8dba-110">4.7.1</span></span>|
|<span data-ttu-id="d8dba-111">類型</span><span class="sxs-lookup"><span data-stu-id="d8dba-111">Type</span></span>|<span data-ttu-id="d8dba-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="d8dba-112">Runtime</span></span>|
