---
ms.openlocfilehash: f61cf21f9f30662cc8e383bb3aeb5c642f1665b8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496778"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a><span data-ttu-id="40041-101">使用可重新進入服務時，可能會造成死結</span><span class="sxs-lookup"><span data-stu-id="40041-101">Deadlock may result when using Reentrant services</span></span>

#### <a name="details"></a><span data-ttu-id="40041-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="40041-102">Details</span></span>

<span data-ttu-id="40041-103">可重新進入服務可能會造成死結，將服務的執行個體限制為一次執行一個執行緒。</span><span class="sxs-lookup"><span data-stu-id="40041-103">A deadlock may result in a Reentrant service, which restricts instances of the service to one thread of execution at a time.</span></span> <span data-ttu-id="40041-104">容易發生此問題的服務在其程式碼中會有下列 <xref:System.ServiceModel.ServiceBehaviorAttribute>：</span><span class="sxs-lookup"><span data-stu-id="40041-104">Services prone to encounter this problem will have the following <xref:System.ServiceModel.ServiceBehaviorAttribute> in their code:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a><span data-ttu-id="40041-105">建議</span><span class="sxs-lookup"><span data-stu-id="40041-105">Suggestion</span></span>

<span data-ttu-id="40041-106">若要解決此問題，您可執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="40041-106">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="40041-107">將服務的並行模式設定為 <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> 或 <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="40041-107">Set the service's concurrency mode to <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> or <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType>.</span></span> <span data-ttu-id="40041-108">例如：</span><span class="sxs-lookup"><span data-stu-id="40041-108">For example:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

- <span data-ttu-id="40041-109">安裝 .NET Framework 4.6.2 的最新更新，或升級至更新版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="40041-109">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="40041-110">這會停用 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 中的 <xref:System.Threading.ExecutionContext> 流程。</span><span class="sxs-lookup"><span data-stu-id="40041-110">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span></span> <span data-ttu-id="40041-111">這是可設定的行為；相當於在您的組態檔中新增下列應用程式設定：</span><span class="sxs-lookup"><span data-stu-id="40041-111">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

```xml
<appSettings>
  <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
</appSettings>
```

<span data-ttu-id="40041-112">Reentrant 服務的值 `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` 絕對不可設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="40041-112">The value of `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` should never be set to `false` for Reentrant services.</span></span>

| <span data-ttu-id="40041-113">名稱</span><span class="sxs-lookup"><span data-stu-id="40041-113">Name</span></span>    | <span data-ttu-id="40041-114">值</span><span class="sxs-lookup"><span data-stu-id="40041-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="40041-115">範圍</span><span class="sxs-lookup"><span data-stu-id="40041-115">Scope</span></span>   | <span data-ttu-id="40041-116">Minor</span><span class="sxs-lookup"><span data-stu-id="40041-116">Minor</span></span>       |
| <span data-ttu-id="40041-117">版本</span><span class="sxs-lookup"><span data-stu-id="40041-117">Version</span></span> | <span data-ttu-id="40041-118">4.6.2</span><span class="sxs-lookup"><span data-stu-id="40041-118">4.6.2</span></span>       |
| <span data-ttu-id="40041-119">類型</span><span class="sxs-lookup"><span data-stu-id="40041-119">Type</span></span>    | <span data-ttu-id="40041-120">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="40041-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="40041-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="40041-121">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType>
