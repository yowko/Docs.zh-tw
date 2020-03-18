---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568253"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="058ff-101">JsonElement API 更改</span><span class="sxs-lookup"><span data-stu-id="058ff-101">JsonElement API changes</span></span>

<span data-ttu-id="058ff-102">從 .NET 核心 3.0 預覽<xref:System.Text.Json.JsonElement>7 開始，一些 API 已更改，以便更輕鬆地發現和增強可用性。</span><span class="sxs-lookup"><span data-stu-id="058ff-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="058ff-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="058ff-103">Change description</span></span>

<span data-ttu-id="058ff-104">在 .NET 核心 3.0<xref:System.Text.Json.JsonElement>預覽 7 中，API 已更改如下，以便更輕鬆地發現和增強可用性。</span><span class="sxs-lookup"><span data-stu-id="058ff-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="058ff-105">從`WriteProperty`<xref:System.Text.Json.JsonElement>中刪除了所有方法重載。</span><span class="sxs-lookup"><span data-stu-id="058ff-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="058ff-106">這會影響以下代碼：</span><span class="sxs-lookup"><span data-stu-id="058ff-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="058ff-107">`WriteValue`被重命名為<xref:System.Text.Json.JsonElement.WriteTo%2A>。</span><span class="sxs-lookup"><span data-stu-id="058ff-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="058ff-108">這會影響以下代碼：</span><span class="sxs-lookup"><span data-stu-id="058ff-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="058ff-109"><xref:System.Text.Json.JsonElement.WriteTo%2A>現在，當它<xref:System.ArgumentNullException>的方法參數為`null`時引發 。</span><span class="sxs-lookup"><span data-stu-id="058ff-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="058ff-110">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="058ff-110">Version introduced</span></span>

<span data-ttu-id="058ff-111">3.0 預覽 7</span><span class="sxs-lookup"><span data-stu-id="058ff-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="058ff-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="058ff-112">Recommended action</span></span>

<span data-ttu-id="058ff-113">如果代碼受到這些更改的影響，您可以執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="058ff-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="058ff-114">中沒有`WriteProperty`替換超載的<xref:System.Text.Json.JsonElement>API。</span><span class="sxs-lookup"><span data-stu-id="058ff-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="058ff-115">相反，您可以調用其中一個<xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType>重載以及<xref:System.Text.Json.JsonElement.WriteTo%2A>方法來實現相同的結果。</span><span class="sxs-lookup"><span data-stu-id="058ff-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achieve the same result.</span></span> <span data-ttu-id="058ff-116">例如：</span><span class="sxs-lookup"><span data-stu-id="058ff-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="058ff-117">將`WriteValue`方法重命名為<xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>。</span><span class="sxs-lookup"><span data-stu-id="058ff-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="058ff-118">方法參數保持不變。</span><span class="sxs-lookup"><span data-stu-id="058ff-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="058ff-119">例如，以前的代碼應更改為以下內容：</span><span class="sxs-lookup"><span data-stu-id="058ff-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="058ff-120">處理對<xref:System.ArgumentNullException>方法的<xref:System.Text.Json.JsonElement.WriteTo%2A>調用。</span><span class="sxs-lookup"><span data-stu-id="058ff-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="058ff-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="058ff-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
