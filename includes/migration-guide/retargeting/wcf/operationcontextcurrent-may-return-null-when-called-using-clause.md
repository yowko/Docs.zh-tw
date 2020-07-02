---
ms.openlocfilehash: d25c14f93da5fe8acf06269554fed30ddc6bc95d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614361"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a><span data-ttu-id="f0217-101">OperationContext.Current 在 using 子句中進行呼叫時，可能會傳回 Null</span><span class="sxs-lookup"><span data-stu-id="f0217-101">OperationContext.Current may return null when called in a using clause</span></span>

#### <a name="details"></a><span data-ttu-id="f0217-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f0217-102">Details</span></span>

<span data-ttu-id="f0217-103">如果符合下列所有條件，則 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 可能會傳回 `null`，而且可能會導致 <xref:System.NullReferenceException>：</span><span class="sxs-lookup"><span data-stu-id="f0217-103"><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> may return `null` and a <xref:System.NullReferenceException> may result if all of the following conditions are true:</span></span>

- <span data-ttu-id="f0217-104">擷取傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 的方法中 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f0217-104">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property in a method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>
- <span data-ttu-id="f0217-105">具現化 `using` 子句中的 <xref:System.ServiceModel.OperationContextScope> 物件。</span><span class="sxs-lookup"><span data-stu-id="f0217-105">You instantiate the <xref:System.ServiceModel.OperationContextScope> object in a `using` clause.</span></span>
- <span data-ttu-id="f0217-106">擷取 `using statement` 內 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f0217-106">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property within the `using statement`.</span></span> <span data-ttu-id="f0217-107">例如：</span><span class="sxs-lookup"><span data-stu-id="f0217-107">For example:</span></span>

```csharp
using (new OperationContextScope(OperationContext.Current))
{
    // OperationContext.Current is null.
    OperationContext context = OperationContext.Current;

    // ...
}
```

#### <a name="suggestion"></a><span data-ttu-id="f0217-108">建議</span><span class="sxs-lookup"><span data-stu-id="f0217-108">Suggestion</span></span>

<span data-ttu-id="f0217-109">若要解決此問題，您可執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="f0217-109">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="f0217-110">如下所示修改您的程式碼，以具現化新的非 `null` <xref:System.ServiceModel.OperationContext.Current%2A> 物件：</span><span class="sxs-lookup"><span data-stu-id="f0217-110">Modify your code as follows to instantiate a new non- `null` <xref:System.ServiceModel.OperationContext.Current%2A> object:</span></span>

    ```csharp
    OperationContext ocx = OperationContext.Current;
    using (new OperationContextScope(OperationContext.Current))
    {
        OperationContext.Current = new OperationContext(ocx.Channel);

        // ...
    }
    ```

- <span data-ttu-id="f0217-111">安裝 .NET Framework 4.6.2 的最新更新，或升級至更新版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="f0217-111">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="f0217-112">這會停用 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 中的 <xref:System.Threading.ExecutionContext> 流程，並還原 WCF 應用程式在 .NET Framework 4.6.1 和舊版中的行為。</span><span class="sxs-lookup"><span data-stu-id="f0217-112">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> and restores the behavior of WCF applications in the .NET Framework 4.6.1 and earlier versions.</span></span> <span data-ttu-id="f0217-113">這是可設定的行為；相當於在您的組態檔中新增下列應用程式設定：</span><span class="sxs-lookup"><span data-stu-id="f0217-113">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
    </appSettings>
    ```

    <span data-ttu-id="f0217-114">如果這項變更並不適當，且您的應用程式相依於作業內容之間流動的執行內容，您可以啟用其流程，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f0217-114">If this change is undesirable and your application depends on execution context flowing between operation contexts, you can enable its flow as follows:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="false" />
    </appSettings>
    ```

| <span data-ttu-id="f0217-115">名稱</span><span class="sxs-lookup"><span data-stu-id="f0217-115">Name</span></span>    | <span data-ttu-id="f0217-116">值</span><span class="sxs-lookup"><span data-stu-id="f0217-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f0217-117">影響範圍</span><span class="sxs-lookup"><span data-stu-id="f0217-117">Scope</span></span>   | <span data-ttu-id="f0217-118">Edge</span><span class="sxs-lookup"><span data-stu-id="f0217-118">Edge</span></span>        |
| <span data-ttu-id="f0217-119">版本</span><span class="sxs-lookup"><span data-stu-id="f0217-119">Version</span></span> | <span data-ttu-id="f0217-120">4.6.2</span><span class="sxs-lookup"><span data-stu-id="f0217-120">4.6.2</span></span>       |
| <span data-ttu-id="f0217-121">類型</span><span class="sxs-lookup"><span data-stu-id="f0217-121">Type</span></span>    | <span data-ttu-id="f0217-122">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="f0217-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f0217-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f0217-123">Affected APIs</span></span>

- <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>
