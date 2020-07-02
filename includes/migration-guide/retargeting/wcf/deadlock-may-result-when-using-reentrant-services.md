---
ms.openlocfilehash: dd7d3e445772e4b5ec148576ccd1374d56e251bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614372"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a><span data-ttu-id="2c36e-101">使用可重新進入服務時，可能會造成死結</span><span class="sxs-lookup"><span data-stu-id="2c36e-101">Deadlock may result when using Reentrant services</span></span>

#### <a name="details"></a><span data-ttu-id="2c36e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2c36e-102">Details</span></span>

<span data-ttu-id="2c36e-103">可重新進入服務可能會造成死結，將服務的執行個體限制為一次執行一個執行緒。</span><span class="sxs-lookup"><span data-stu-id="2c36e-103">A deadlock may result in a Reentrant service, which restricts instances of the service to one thread of execution at a time.</span></span> <span data-ttu-id="2c36e-104">容易發生此問題的服務在其程式碼中會有下列 <xref:System.ServiceModel.ServiceBehaviorAttribute>：</span><span class="sxs-lookup"><span data-stu-id="2c36e-104">Services prone to encounter this problem will have the following <xref:System.ServiceModel.ServiceBehaviorAttribute> in their code:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a><span data-ttu-id="2c36e-105">建議</span><span class="sxs-lookup"><span data-stu-id="2c36e-105">Suggestion</span></span>

<span data-ttu-id="2c36e-106">若要解決此問題，您可執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="2c36e-106">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="2c36e-107">將服務的並行模式設為 <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> 或 &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;。</span><span class="sxs-lookup"><span data-stu-id="2c36e-107">Set the service's concurrency mode to <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> or &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;.</span></span> <span data-ttu-id="2c36e-108">例如：</span><span class="sxs-lookup"><span data-stu-id="2c36e-108">For example:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

- <span data-ttu-id="2c36e-109">安裝 .NET Framework 4.6.2 的最新更新，或升級至更新版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="2c36e-109">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="2c36e-110">這會停用 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 中的 <xref:System.Threading.ExecutionContext> 流程。</span><span class="sxs-lookup"><span data-stu-id="2c36e-110">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2c36e-111">這是可設定的行為；相當於在您的組態檔中新增下列應用程式設定：</span><span class="sxs-lookup"><span data-stu-id="2c36e-111">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

```xml
<appSettings>
  <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
</appSettings>
```

<span data-ttu-id="2c36e-112">Reentrant 服務的值 `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` 絕對不可設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="2c36e-112">The value of `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` should never be set to `false` for Reentrant services.</span></span>

| <span data-ttu-id="2c36e-113">名稱</span><span class="sxs-lookup"><span data-stu-id="2c36e-113">Name</span></span>    | <span data-ttu-id="2c36e-114">值</span><span class="sxs-lookup"><span data-stu-id="2c36e-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2c36e-115">影響範圍</span><span class="sxs-lookup"><span data-stu-id="2c36e-115">Scope</span></span>   | <span data-ttu-id="2c36e-116">Minor</span><span class="sxs-lookup"><span data-stu-id="2c36e-116">Minor</span></span>       |
| <span data-ttu-id="2c36e-117">版本</span><span class="sxs-lookup"><span data-stu-id="2c36e-117">Version</span></span> | <span data-ttu-id="2c36e-118">4.6.2</span><span class="sxs-lookup"><span data-stu-id="2c36e-118">4.6.2</span></span>       |
| <span data-ttu-id="2c36e-119">類型</span><span class="sxs-lookup"><span data-stu-id="2c36e-119">Type</span></span>    | <span data-ttu-id="2c36e-120">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="2c36e-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="2c36e-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2c36e-121">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType>
