---
ms.openlocfilehash: bba9659b92e5aabc276c585929c99898316036c5
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359127"
---
### <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a><span data-ttu-id="fe127-101">巢狀型別的硬體內部 IsSupported 檢查可能不同</span><span class="sxs-lookup"><span data-stu-id="fe127-101">Hardware intrinsic IsSupported checks may differ for nested types</span></span>

<span data-ttu-id="fe127-102">檢查 `<Isa>.X64.IsSupported` （其中 `<Isa>` 參考命名空間中的類別 <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> ），現在可能會產生與舊版 .net 不同的結果。</span><span class="sxs-lookup"><span data-stu-id="fe127-102">Checking `<Isa>.X64.IsSupported`, where `<Isa>` refers to the classes in the <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> namespace, may now produce a different result to previous versions of .NET.</span></span>

> [!TIP]
> <span data-ttu-id="fe127-103">*ISA* 代表業界標準架構。</span><span class="sxs-lookup"><span data-stu-id="fe127-103">*ISA* stands for industry standard architecture.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fe127-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="fe127-104">Version introduced</span></span>

<span data-ttu-id="fe127-105">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="fe127-105">5.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="fe127-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="fe127-106">Change description</span></span>

<span data-ttu-id="fe127-107">在舊版的 .NET 中，某些硬體內 <xref:System.Runtime.Intrinsics.X86> 建類型（例如）不會 <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType> 公開嵌套 `X64` 類別。</span><span class="sxs-lookup"><span data-stu-id="fe127-107">In previous versions of .NET, some of the <xref:System.Runtime.Intrinsics.X86> hardware-intrinsic types, for example, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType>, didn't expose a nested `X64` class.</span></span> <span data-ttu-id="fe127-108">針對這些類型，呼叫會 `<Isa>.X64.IsSupported` 解析為的 `IsSupported` 父類別的嵌套類別上的屬性 `X64` `<Isa>` 。</span><span class="sxs-lookup"><span data-stu-id="fe127-108">For these types, calling `<Isa>.X64.IsSupported` resolved to an `IsSupported` property on a nested `X64` class of a parent class of `<Isa>`.</span></span> <span data-ttu-id="fe127-109">這表示即使傳回，屬性也可以傳回 `true` `<Isa>.IsSupported` `false` 。</span><span class="sxs-lookup"><span data-stu-id="fe127-109">This meant that the property could return `true` even when `<Isa>.IsSupported` returns `false`.</span></span>

<span data-ttu-id="fe127-110">在 .NET 5.0 和更新版本中，所有 <xref:System.Runtime.Intrinsics.X86> 類型都會公開 `X64` 適當報告支援的嵌套類別。</span><span class="sxs-lookup"><span data-stu-id="fe127-110">In .NET 5.0 and later versions, all of the <xref:System.Runtime.Intrinsics.X86> types expose a nested `X64` class that appropriately reports support.</span></span> <span data-ttu-id="fe127-111">這可確保一般階層保持正確，而且如果 `<Isa>.X64.IsSupported` 是 `true` ，則 `<Isa>.IsSupported` 也可以假設為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="fe127-111">This ensures that the general hierarchy remains correct, and that if `<Isa>.X64.IsSupported` is `true`, then `<Isa>.IsSupported` can also be assumed to be `true`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fe127-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="fe127-112">Reason for change</span></span>

<span data-ttu-id="fe127-113">它的目標是 `<Isa>.X64.IsSupported` ，如果是 `true` ，也會 `<Isa>.IsSupported` 隱含為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="fe127-113">It was intended that if `<Isa>.X64.IsSupported` is `true`, `<Isa>.IsSupported` is also implied to be `true`.</span></span> <span data-ttu-id="fe127-114">不過，由於成員解析在 c # 中的運作方式，沒有嵌套類別的類別會 `X64` 公開一種情況，而這種情況不一定會發生，而且會導致使用者程式碼中的 bug。</span><span class="sxs-lookup"><span data-stu-id="fe127-114">However, due to how member resolution works in C#, classes that didn't have a nested `X64` class exposed a situation where this wasn't always the case and led to bugs in user code.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fe127-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="fe127-115">Recommended action</span></span>

<span data-ttu-id="fe127-116">如有必要，請調整檢查 `IsSupported` 以檢查適當 ISA 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fe127-116">If necessary, adjust code that checks `IsSupported` to check for the appropriate ISA.</span></span>

#### <a name="category"></a><span data-ttu-id="fe127-117">類別</span><span class="sxs-lookup"><span data-stu-id="fe127-117">Category</span></span>

<span data-ttu-id="fe127-118">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="fe127-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fe127-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="fe127-119">Affected APIs</span></span>

- <xref:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported`

-->
