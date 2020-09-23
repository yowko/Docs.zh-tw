---
ms.openlocfilehash: 9f5f238e3d4222af1da3a1713e1b3e65de6e6f49
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "91025342"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="867a8-101">WCF PipeConnection.GetHashAlgorithm 現在會使用 SHA256</span><span class="sxs-lookup"><span data-stu-id="867a8-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="867a8-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="867a8-102">Details</span></span>

<span data-ttu-id="867a8-103">從 .NET Framework 4.7.1 開始，Windows Communication Foundation 會使用 SHA256 雜湊來產生具名管道的隨機名稱。</span><span class="sxs-lookup"><span data-stu-id="867a8-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="867a8-104">在 .NET Framework 4.7 和舊版中，它已使用 SHA1 雜湊。</span><span class="sxs-lookup"><span data-stu-id="867a8-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="867a8-105">建議</span><span class="sxs-lookup"><span data-stu-id="867a8-105">Suggestion</span></span>

<span data-ttu-id="867a8-106">如果在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以在 app.config 檔案的 `<runtime>` 區段中新增下列程式行來退出變更：</span><span class="sxs-lookup"><span data-stu-id="867a8-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the `<runtime>` section of your app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="867a8-107">Name</span><span class="sxs-lookup"><span data-stu-id="867a8-107">Name</span></span>    | <span data-ttu-id="867a8-108">值</span><span class="sxs-lookup"><span data-stu-id="867a8-108">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="867a8-109">範圍</span><span class="sxs-lookup"><span data-stu-id="867a8-109">Scope</span></span>   | <span data-ttu-id="867a8-110">Minor</span><span class="sxs-lookup"><span data-stu-id="867a8-110">Minor</span></span>   |
| <span data-ttu-id="867a8-111">版本</span><span class="sxs-lookup"><span data-stu-id="867a8-111">Version</span></span> | <span data-ttu-id="867a8-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="867a8-112">4.7.1</span></span>   |
| <span data-ttu-id="867a8-113">類型</span><span class="sxs-lookup"><span data-stu-id="867a8-113">Type</span></span>    | <span data-ttu-id="867a8-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="867a8-114">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="867a8-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="867a8-115">Affected APIs</span></span>

<span data-ttu-id="867a8-116">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="867a8-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
