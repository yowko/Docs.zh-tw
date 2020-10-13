---
ms.openlocfilehash: 572ebc47d26e30738fc4e5b8a8fab1f2643e3d83
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997706"
---
### <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a><span data-ttu-id="86427-101">非公用、無參數的函式不會用於還原序列化</span><span class="sxs-lookup"><span data-stu-id="86427-101">Non-public, parameterless constructors not used for deserialization</span></span>

<span data-ttu-id="86427-102">為了在所有支援的目標 framework 標記之間保持一致性 (Tfm) ，非公用的無參數函式預設不會再用於還原序列化 <xref:System.Text.Json.JsonSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="86427-102">For consistency across all supported target framework monikers (TFMs), non-public, parameterless constructors are no longer used for deserialization with <xref:System.Text.Json.JsonSerializer>, by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="86427-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="86427-103">Change description</span></span>

<span data-ttu-id="86427-104">在 .NET Core 3.0 和3.1 上，內部和私用的函式可用於還原序列化。</span><span class="sxs-lookup"><span data-stu-id="86427-104">On .NET Core 3.0 and 3.1, internal and private constructors can be used for deserialization.</span></span> <span data-ttu-id="86427-105">在 .NET Standard 2.0 和2.1 上，不允許內部和私用的函式，而且 <xref:System.MissingMethodException> 如果沒有定義任何公用的無參數的函式，就會擲回。</span><span class="sxs-lookup"><span data-stu-id="86427-105">On .NET Standard 2.0 and 2.1, internal and private constructors are not allowed, and a <xref:System.MissingMethodException> is thrown if no public, parameterless constructor is defined.</span></span>

<span data-ttu-id="86427-106">從 .NET 5.0 開始，序列化程式預設會忽略非公用的函式（包括無參數的函式）。</span><span class="sxs-lookup"><span data-stu-id="86427-106">Starting in .NET 5.0, non-public constructors, including parameterless constructors, are ignored by the serializer by default.</span></span> <span data-ttu-id="86427-107">序列化程式會使用下列其中一個用於還原序列化的函式：</span><span class="sxs-lookup"><span data-stu-id="86427-107">The serializer uses one of the following constructors for deserialization:</span></span>

- <span data-ttu-id="86427-108">使用批註的公用函式 <xref:System.Text.Json.Serialization.JsonConstructorAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="86427-108">Public constructor annotated with <xref:System.Text.Json.Serialization.JsonConstructorAttribute>.</span></span>
- <span data-ttu-id="86427-109">公用無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="86427-109">Public parameterless constructor.</span></span>
- <span data-ttu-id="86427-110">公用參數化的函式 (是否為唯一的公用函式) 。</span><span class="sxs-lookup"><span data-stu-id="86427-110">Public parameterized constructor (if it's the only public constructor present).</span></span>

<span data-ttu-id="86427-111">如果沒有這些可用的函式， <xref:System.NotSupportedException> 當您嘗試還原序列化類型時，就會擲回。</span><span class="sxs-lookup"><span data-stu-id="86427-111">If none of these constructors are available, a <xref:System.NotSupportedException> is thrown if you attempt to deserialize the type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="86427-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="86427-112">Version introduced</span></span>

<span data-ttu-id="86427-113">5.0</span><span class="sxs-lookup"><span data-stu-id="86427-113">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="86427-114">變更的原因</span><span class="sxs-lookup"><span data-stu-id="86427-114">Reason for change</span></span>

- <span data-ttu-id="86427-115">若要在所有目標 framework 標記之間強制執行一致的行為 (可為 <xref:System.Text.Json?displayProperty=fullName> ( .Net Core 3.0 和更新版本所建立的 tfm) ，以及 .NET Standard 2.0 和 2.1) </span><span class="sxs-lookup"><span data-stu-id="86427-115">To enforce consistent behavior between all target framework monikers (TFMs) that <xref:System.Text.Json?displayProperty=fullName> builds for (.NET Core 3.0 and later versions, and .NET Standard 2.0 and 2.1)</span></span>
- <span data-ttu-id="86427-116">因為 <xref:System.Text.Json.JsonSerializer> 不應該呼叫類型的非公用介面區，無論是函式、屬性或欄位。</span><span class="sxs-lookup"><span data-stu-id="86427-116">Because <xref:System.Text.Json.JsonSerializer> shouldn't call the non-public surface area of a type, whether that's a constructor, a property, or a field.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="86427-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="86427-117">Recommended action</span></span>

- <span data-ttu-id="86427-118">如果您擁有類型且可行，請將無參數的函式設為公用。</span><span class="sxs-lookup"><span data-stu-id="86427-118">If you own the type and it's feasible, make the parameterless constructor public.</span></span>
- <span data-ttu-id="86427-119">否則，請 `JsonConverter<T>` 針對類型執行，並控制還原序列化行為。</span><span class="sxs-lookup"><span data-stu-id="86427-119">Otherwise, implement a `JsonConverter<T>` for the type and control the deserialization behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="86427-120">類別</span><span class="sxs-lookup"><span data-stu-id="86427-120">Category</span></span>

<span data-ttu-id="86427-121">序列化</span><span class="sxs-lookup"><span data-stu-id="86427-121">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="86427-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="86427-122">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
