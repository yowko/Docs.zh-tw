---
ms.openlocfilehash: 7c0227980aa5d90f3788783088bcd7cd9509ed66
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770829"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="fe303-101">WCF MsmqSecureHashAlgorithm 預設值現在是 SHA256</span><span class="sxs-lookup"><span data-stu-id="fe303-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="fe303-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fe303-102">Details</span></span>

<span data-ttu-id="fe303-103">從 .NET Framework 4.7.1 開始，WCF 中用於 Msmq 訊息的預設訊息簽署演算法是 SHA256。</span><span class="sxs-lookup"><span data-stu-id="fe303-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="fe303-104">在 .NET Framework 4.7 和舊版中，預設的訊息簽署演算法是 SHA1。</span><span class="sxs-lookup"><span data-stu-id="fe303-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fe303-105">建議</span><span class="sxs-lookup"><span data-stu-id="fe303-105">Suggestion</span></span>

<span data-ttu-id="fe303-106">如果您在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以在 app.config 檔案的區段中加入下列這一行，以退出宣告變更 `<runtime>` ：</span><span class="sxs-lookup"><span data-stu-id="fe303-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the `<runtime>` section of your app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; />
  </runtime>
</configuration>
```

| <span data-ttu-id="fe303-107">Name</span><span class="sxs-lookup"><span data-stu-id="fe303-107">Name</span></span>    | <span data-ttu-id="fe303-108">值</span><span class="sxs-lookup"><span data-stu-id="fe303-108">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="fe303-109">範圍</span><span class="sxs-lookup"><span data-stu-id="fe303-109">Scope</span></span>   | <span data-ttu-id="fe303-110">Minor</span><span class="sxs-lookup"><span data-stu-id="fe303-110">Minor</span></span>   |
| <span data-ttu-id="fe303-111">版本</span><span class="sxs-lookup"><span data-stu-id="fe303-111">Version</span></span> | <span data-ttu-id="fe303-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="fe303-112">4.7.1</span></span>   |
| <span data-ttu-id="fe303-113">類型</span><span class="sxs-lookup"><span data-stu-id="fe303-113">Type</span></span>    | <span data-ttu-id="fe303-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="fe303-114">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="fe303-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="fe303-115">Affected APIs</span></span>

<span data-ttu-id="fe303-116">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="fe303-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
