---
ms.openlocfilehash: d25c14f93da5fe8acf06269554fed30ddc6bc95d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614361"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext.Current 在 using 子句中進行呼叫時，可能會傳回 Null

#### <a name="details"></a>詳細資料

如果符合下列所有條件，則 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 可能會傳回 `null`，而且可能會導致 <xref:System.NullReferenceException>：

- 擷取傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 的方法中 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 屬性的值。
- 具現化 `using` 子句中的 <xref:System.ServiceModel.OperationContextScope> 物件。
- 擷取 `using statement` 內 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 屬性的值。 例如：

```csharp
using (new OperationContextScope(OperationContext.Current))
{
    // OperationContext.Current is null.
    OperationContext context = OperationContext.Current;

    // ...
}
```

#### <a name="suggestion"></a>建議

若要解決此問題，您可執行以下動作：

- 如下所示修改您的程式碼，以具現化新的非 `null` <xref:System.ServiceModel.OperationContext.Current%2A> 物件：

    ```csharp
    OperationContext ocx = OperationContext.Current;
    using (new OperationContextScope(OperationContext.Current))
    {
        OperationContext.Current = new OperationContext(ocx.Channel);

        // ...
    }
    ```

- 安裝 .NET Framework 4.6.2 的最新更新，或升級至更新版本的 .NET Framework。 這會停用 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 中的 <xref:System.Threading.ExecutionContext> 流程，並還原 WCF 應用程式在 .NET Framework 4.6.1 和舊版中的行為。 這是可設定的行為；相當於在您的組態檔中新增下列應用程式設定：

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
    </appSettings>
    ```

    如果這項變更並不適當，且您的應用程式相依於作業內容之間流動的執行內容，您可以啟用其流程，如下所示：

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="false" />
    </appSettings>
    ```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.6.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>
