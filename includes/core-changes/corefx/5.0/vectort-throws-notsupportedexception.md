---
ms.openlocfilehash: 43ebb37124b8efe077b9f81fe5351bd7db2c72f7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302700"
---
### <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a><span data-ttu-id="07de2-101">Vector \<T> 一律會針對不支援的類型擲回 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="07de2-101">Vector\<T> always throws NotSupportedException for unsupported types</span></span>

<span data-ttu-id="07de2-102"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> 現在一律會 <xref:System.NotSupportedException> 針對不支援的類型參數擲回。</span><span class="sxs-lookup"><span data-stu-id="07de2-102"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> now always throws a <xref:System.NotSupportedException> for unsupported type parameters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="07de2-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="07de2-103">Change description</span></span>

<span data-ttu-id="07de2-104">先前的成員 <xref:System.Numerics.Vector%601> <xref:System.NotSupportedException> 在不 `T` [受支援的類型](#unsupported-types)時，不一定會擲回。</span><span class="sxs-lookup"><span data-stu-id="07de2-104">Previously, members of <xref:System.Numerics.Vector%601> would not always throw a <xref:System.NotSupportedException> when `T` was an [unsupported type](#unsupported-types).</span></span> <span data-ttu-id="07de2-105">由於支援硬體加速的程式碼路徑，因此不一定會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="07de2-105">The exception wasn't always thrown because of code paths that supported hardware acceleration.</span></span> <span data-ttu-id="07de2-106">例如， `Vector<bool> + Vector<bool>` 會傳回， `default` 而不是在沒有硬體加速的平臺上擲回例外狀況，例如 ARM32。</span><span class="sxs-lookup"><span data-stu-id="07de2-106">For example, `Vector<bool> + Vector<bool>` returned `default` instead of throwing an exception on platforms that have no hardware acceleration, such as ARM32.</span></span> <span data-ttu-id="07de2-107">針對不支援的類型， <xref:System.Numerics.Vector%601> 成員會在不同的平臺和硬體設定之間呈現不一致的行為。</span><span class="sxs-lookup"><span data-stu-id="07de2-107">For unsupported types, <xref:System.Numerics.Vector%601> members exhibited inconsistent behavior across different platforms and hardware configurations.</span></span>

<span data-ttu-id="07de2-108">從 .NET 5.0 開始， <xref:System.Numerics.Vector%601> 當不是支援的類型時，成員一律 <xref:System.NotSupportedException> 會在所有硬體設定上擲回 `T` 。</span><span class="sxs-lookup"><span data-stu-id="07de2-108">Starting in .NET 5.0, <xref:System.Numerics.Vector%601> members always throw a <xref:System.NotSupportedException> on all hardware configurations when `T` is not a supported type.</span></span>

##### <a name="unsupported-types"></a><span data-ttu-id="07de2-109">不支援的類型</span><span class="sxs-lookup"><span data-stu-id="07de2-109">Unsupported types</span></span>

<span data-ttu-id="07de2-110">的類型參數支援的類型 <xref:System.Numerics.Vector%601> 為：</span><span class="sxs-lookup"><span data-stu-id="07de2-110">The supported types for the type parameter of <xref:System.Numerics.Vector%601> are:</span></span>

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

<span data-ttu-id="07de2-111">但支援的類型尚未變更，但未來可能會變更。</span><span class="sxs-lookup"><span data-stu-id="07de2-111">The supported types have not changed, however, they may change in the future.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="07de2-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="07de2-112">Version introduced</span></span>

<span data-ttu-id="07de2-113">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="07de2-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="07de2-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="07de2-114">Recommended action</span></span>

<span data-ttu-id="07de2-115">請勿針對的型別參數使用不支援的類型 <xref:System.Numerics.Vector%601> 。</span><span class="sxs-lookup"><span data-stu-id="07de2-115">Don't use an unsupported type for the type parameter of <xref:System.Numerics.Vector%601>.</span></span>

#### <a name="category"></a><span data-ttu-id="07de2-116">類別</span><span class="sxs-lookup"><span data-stu-id="07de2-116">Category</span></span>

<span data-ttu-id="07de2-117">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="07de2-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="07de2-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="07de2-118">Affected APIs</span></span>

- <span data-ttu-id="07de2-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> 及其所有成員</span><span class="sxs-lookup"><span data-stu-id="07de2-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> and all its members</span></span>

<!--

#### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
