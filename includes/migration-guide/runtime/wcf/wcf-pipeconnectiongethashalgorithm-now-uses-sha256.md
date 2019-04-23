---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803482"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="6ea4e-101">WCF PipeConnection.GetHashAlgorithm 現在會使用 SHA256</span><span class="sxs-lookup"><span data-stu-id="6ea4e-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6ea4e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6ea4e-102">Details</span></span>|<span data-ttu-id="6ea4e-103">從 .NET Framework 4.7.1 開始，Windows Communication Foundation 會使用 SHA256 雜湊來產生具名管道的隨機名稱。</span><span class="sxs-lookup"><span data-stu-id="6ea4e-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="6ea4e-104">在 .NET Framework 4.7 和舊版中，它已使用 SHA1 雜湊。</span><span class="sxs-lookup"><span data-stu-id="6ea4e-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>|
|<span data-ttu-id="6ea4e-105">建議</span><span class="sxs-lookup"><span data-stu-id="6ea4e-105">Suggestion</span></span>|<span data-ttu-id="6ea4e-106">如果在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以在 app.config 檔案的 <code>&lt;runtime&gt;</code> 區段中新增下列程式行來退出變更：</span><span class="sxs-lookup"><span data-stu-id="6ea4e-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="6ea4e-107">範圍</span><span class="sxs-lookup"><span data-stu-id="6ea4e-107">Scope</span></span>|<span data-ttu-id="6ea4e-108">次要</span><span class="sxs-lookup"><span data-stu-id="6ea4e-108">Minor</span></span>|
|<span data-ttu-id="6ea4e-109">版本</span><span class="sxs-lookup"><span data-stu-id="6ea4e-109">Version</span></span>|<span data-ttu-id="6ea4e-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="6ea4e-110">4.7.1</span></span>|
|<span data-ttu-id="6ea4e-111">類型</span><span class="sxs-lookup"><span data-stu-id="6ea4e-111">Type</span></span>|<span data-ttu-id="6ea4e-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="6ea4e-112">Runtime</span></span>|
