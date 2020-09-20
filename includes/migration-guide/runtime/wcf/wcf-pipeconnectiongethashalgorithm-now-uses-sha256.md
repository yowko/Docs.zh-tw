---
ms.openlocfilehash: 3cf1740565343558a85fdfa68957773468c28231
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770804"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="e6c3e-101">WCF PipeConnection.GetHashAlgorithm 現在會使用 SHA256</span><span class="sxs-lookup"><span data-stu-id="e6c3e-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="e6c3e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e6c3e-102">Details</span></span>

<span data-ttu-id="e6c3e-103">從 .NET Framework 4.7.1 開始，Windows Communication Foundation 會使用 SHA256 雜湊來產生具名管道的隨機名稱。</span><span class="sxs-lookup"><span data-stu-id="e6c3e-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="e6c3e-104">在 .NET Framework 4.7 和舊版中，它已使用 SHA1 雜湊。</span><span class="sxs-lookup"><span data-stu-id="e6c3e-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e6c3e-105">建議</span><span class="sxs-lookup"><span data-stu-id="e6c3e-105">Suggestion</span></span>

<span data-ttu-id="e6c3e-106">如果在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以在 app.config 檔案的 `<runtime>` 區段中新增下列程式行來退出變更：</span><span class="sxs-lookup"><span data-stu-id="e6c3e-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the `<runtime>` section of your app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true" />
  </runtime>
</configuration>

| Name    | Value   |
|:--------|:--------|
| Scope   | Minor   |
| Version | 4.7.1   |
| Type    | Runtime |

#### Affected APIs

Not detectable via API analysis.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
