---
ms.openlocfilehash: 98893470b64de4abf7f04817871e3053bf25b86d
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119300"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="bf819-101">JsonElement API 變更</span><span class="sxs-lookup"><span data-stu-id="bf819-101">JsonElement API changes</span></span>

<span data-ttu-id="bf819-102">從 .net Core 3.0 Preview 7 開始，某些<xref:System.Text.Json.JsonElement> api 已變更為允許更輕鬆的探索和更高的可用性。</span><span class="sxs-lookup"><span data-stu-id="bf819-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bf819-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="bf819-103">Change description</span></span>

<span data-ttu-id="bf819-104">在 .net Core 3.0 Preview 7 中<xref:System.Text.Json.JsonElement> ，api 已依照下列方式變更，以允許更容易探索及使用更高的可用性。</span><span class="sxs-lookup"><span data-stu-id="bf819-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="bf819-105">已`WriteProperty` 從<xref:System.Text.Json.JsonElement>移除所有方法多載。</span><span class="sxs-lookup"><span data-stu-id="bf819-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="bf819-106">這會影響程式碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf819-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="bf819-107">`WriteValue`已重新命名<xref:System.Text.Json.JsonElement.WriteTo%2A>為。</span><span class="sxs-lookup"><span data-stu-id="bf819-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="bf819-108">這會影響程式碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf819-108">This affects code such as the following:</span></span>

```csharp
using (JsonDocument doc = JsonDocument.Parse(jsonString))
{
    JsonElement root = doc.RootElement;
    root.WriteValue(writer);
}

```

1. <span data-ttu-id="bf819-109"><xref:System.Text.Json.JsonElement.WriteTo%2A>現在， `null`當其方法參數為時，會擲回。 <xref:System.ArgumentNullException></span><span class="sxs-lookup"><span data-stu-id="bf819-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bf819-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="bf819-110">Version introduced</span></span>

<span data-ttu-id="bf819-111">3.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="bf819-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bf819-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bf819-112">Recommended action</span></span>

<span data-ttu-id="bf819-113">如果您的程式碼受到這些變更的影響，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="bf819-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="bf819-114">`WriteProperty` 中<xref:System.Text.Json.JsonElement>的多載沒有替代 API。</span><span class="sxs-lookup"><span data-stu-id="bf819-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="bf819-115">相反地，您可以呼叫其中一個<xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType>多載以及<xref:System.Text.Json.JsonElement.WriteTo%2A>方法，以達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="bf819-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achive the same result.</span></span> <span data-ttu-id="bf819-116">例如：</span><span class="sxs-lookup"><span data-stu-id="bf819-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="bf819-117">將方法重新命名<xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>為。 `WriteValue`</span><span class="sxs-lookup"><span data-stu-id="bf819-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="bf819-118">方法參數會保持不變。</span><span class="sxs-lookup"><span data-stu-id="bf819-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="bf819-119">例如，先前的程式碼應該變更為下列內容：</span><span class="sxs-lookup"><span data-stu-id="bf819-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="bf819-120"><xref:System.ArgumentNullException>在<xref:System.Text.Json.JsonElement.WriteTo%2A>方法的呼叫中處理。</span><span class="sxs-lookup"><span data-stu-id="bf819-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bf819-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bf819-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
