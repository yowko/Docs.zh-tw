---
ms.openlocfilehash: f61e5670334f4d3674fd0b008d1a476b14c7ba4e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496984"
---
### <a name="calling-attributegetcustomattributes-on-an-indexer-property-no-longer-throws-ambiguousmatchexception-if-the-ambiguity-can-be-resolved-by-indexs-type"></a><span data-ttu-id="5882d-101">如果索引類型可解決語意模糊，在索引子屬性上呼叫 Attribute.GetCustomAttributes 不會再擲回 AmbiguousMatchException</span><span class="sxs-lookup"><span data-stu-id="5882d-101">Calling Attribute.GetCustomAttributes on an indexer property no longer throws AmbiguousMatchException if the ambiguity can be resolved by index's type</span></span>

#### <a name="details"></a><span data-ttu-id="5882d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5882d-102">Details</span></span>

<span data-ttu-id="5882d-103">在 .NET Framework 4.6 之前，在索引子屬性上呼叫 <code>GetCustomAttribute(s)</code>，而且該索引子屬性與其他屬性只有索引類型不同時，會造成 <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="5882d-103">Prior to the .NET Framework 4.6, calling <code>GetCustomAttribute(s)</code> on an indexer property which differed from another property only by the type of the index would result in an <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>.</span></span> <span data-ttu-id="5882d-104">從 .NET Framework 4.6 開始，將會正確地傳回屬性 (Property) 的屬性 (Attributee)。</span><span class="sxs-lookup"><span data-stu-id="5882d-104">Beginning in the .NET Framework 4.6, the property's attributes will be correctly returned.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5882d-105">建議</span><span class="sxs-lookup"><span data-stu-id="5882d-105">Suggestion</span></span>

<span data-ttu-id="5882d-106">請注意，GetCustomAttribute 現在正常運作的頻率會更高。</span><span class="sxs-lookup"><span data-stu-id="5882d-106">Be aware that GetCustomAttribute(s) will work more frequently now.</span></span> <span data-ttu-id="5882d-107">如果應用程式先前依賴 <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>，現在應該改用反映來明確尋找多個索引子。</span><span class="sxs-lookup"><span data-stu-id="5882d-107">If an app was previously relying on the <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>, reflection should now be used to explicitly look for multiple indexers, instead.</span></span>

| <span data-ttu-id="5882d-108">名稱</span><span class="sxs-lookup"><span data-stu-id="5882d-108">Name</span></span>    | <span data-ttu-id="5882d-109">值</span><span class="sxs-lookup"><span data-stu-id="5882d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5882d-110">範圍</span><span class="sxs-lookup"><span data-stu-id="5882d-110">Scope</span></span>   |<span data-ttu-id="5882d-111">Edge</span><span class="sxs-lookup"><span data-stu-id="5882d-111">Edge</span></span>|
|<span data-ttu-id="5882d-112">版本</span><span class="sxs-lookup"><span data-stu-id="5882d-112">Version</span></span>|<span data-ttu-id="5882d-113">4.6</span><span class="sxs-lookup"><span data-stu-id="5882d-113">4.6</span></span>|
|<span data-ttu-id="5882d-114">類型</span><span class="sxs-lookup"><span data-stu-id="5882d-114">Type</span></span>|<span data-ttu-id="5882d-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="5882d-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5882d-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5882d-116">Affected APIs</span></span>

- <xref:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)`
- `M:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute``1(System.Reflection.MemberInfo)``
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute``1(System.Reflection.MemberInfo,System.Boolean)``
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes``1(System.Reflection.MemberInfo)``
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes``1(System.Reflection.MemberInfo,System.Boolean)``

-->
