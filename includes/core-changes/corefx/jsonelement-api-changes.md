---
ms.openlocfilehash: 8a92a426ac2c5eee6fba40bfc46281420466d648
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237316"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="df694-101">JsonElement API 變更</span><span class="sxs-lookup"><span data-stu-id="df694-101">JsonElement API changes</span></span>

<span data-ttu-id="df694-102">從 .NET Core 3.0 Preview 7 開始，部分 <xref:System.Text.Json.JsonElement> Api 已變更為允許更輕鬆的探索和更高的可用性。</span><span class="sxs-lookup"><span data-stu-id="df694-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="df694-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="df694-103">Change description</span></span>

<span data-ttu-id="df694-104">在 .NET Core 3.0 Preview 7 中，<xref:System.Text.Json.JsonElement> Api 已依照下列方式變更，以允許更容易探索及使用更高的可用性。</span><span class="sxs-lookup"><span data-stu-id="df694-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="df694-105">已從 <xref:System.Text.Json.JsonElement>移除所有 `WriteProperty` 方法多載。</span><span class="sxs-lookup"><span data-stu-id="df694-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="df694-106">這會影響程式碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="df694-106">This affects code such as the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
      JsonElement root = doc.RootElement;
      root.WriteProperty(propertyNameString, writer);
      // ..
      root.WriteProperty(propertyNameSpan, writer);
      // ..
      root.WriteProperty(propertyNameJsonEncoded, writer);
      // ..
      root.WriteProperty(utf8PropertyName, writer);
      //..
   }
   ```

1. <span data-ttu-id="df694-107">`WriteValue` 已重新命名為 <xref:System.Text.Json.JsonElement.WriteTo%2A>。</span><span class="sxs-lookup"><span data-stu-id="df694-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="df694-108">這會影響程式碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="df694-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="df694-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> 現在會在 `null`其方法參數時擲回 <xref:System.ArgumentNullException>。</span><span class="sxs-lookup"><span data-stu-id="df694-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="df694-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="df694-110">Version introduced</span></span>

<span data-ttu-id="df694-111">3.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="df694-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="df694-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="df694-112">Recommended action</span></span>

<span data-ttu-id="df694-113">如果您的程式碼受到這些變更的影響，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="df694-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="df694-114"><xref:System.Text.Json.JsonElement>中沒有適用于 `WriteProperty` 多載的替代 API。</span><span class="sxs-lookup"><span data-stu-id="df694-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="df694-115">相反地，您可以呼叫其中一個 <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> 多載以及 <xref:System.Text.Json.JsonElement.WriteTo%2A> 方法，以達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="df694-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achive the same result.</span></span> <span data-ttu-id="df694-116">例如，</span><span class="sxs-lookup"><span data-stu-id="df694-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="df694-117">將 `WriteValue` 方法重新命名為 <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>。</span><span class="sxs-lookup"><span data-stu-id="df694-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="df694-118">方法參數會保持不變。</span><span class="sxs-lookup"><span data-stu-id="df694-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="df694-119">例如，先前的程式碼應該變更為下列內容：</span><span class="sxs-lookup"><span data-stu-id="df694-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="df694-120">處理 <xref:System.Text.Json.JsonElement.WriteTo%2A> 方法呼叫中的 <xref:System.ArgumentNullException>。</span><span class="sxs-lookup"><span data-stu-id="df694-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="df694-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="df694-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
