---
title: -refonly (C# 編譯器選項)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: c380df1cb473fcd187e56bb0a338a909dd3ac894
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="9b07a-102">-refonly (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="9b07a-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="9b07a-103">**-refonly** 選項指出參考組件應是主要輸出的輸出，而不是實作組件。</span><span class="sxs-lookup"><span data-stu-id="9b07a-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="9b07a-104">`-refonly` 參數以無訊息模式停用輸出 PDB，因為無法執行參考組件。</span><span class="sxs-lookup"><span data-stu-id="9b07a-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="9b07a-105">語法</span><span class="sxs-lookup"><span data-stu-id="9b07a-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="9b07a-106">備註</span><span class="sxs-lookup"><span data-stu-id="9b07a-106">Remarks</span></span>

<span data-ttu-id="9b07a-107">僅中繼資料組件以單一的 `throw null` 主體取代其方法主體，但包含匿名型別以外的所有成員。</span><span class="sxs-lookup"><span data-stu-id="9b07a-107">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="9b07a-108">使用 `throw null` 主體的原因 (相對於沒有主體)，是這樣 PEVerify 便可執行和傳遞 (因此驗證中繼資料的完整性)。</span><span class="sxs-lookup"><span data-stu-id="9b07a-108">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="9b07a-109">參考組件包含組件層級的 `ReferenceAssembly` 屬性。</span><span class="sxs-lookup"><span data-stu-id="9b07a-109">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="9b07a-110">這個屬性可在來源中指定 (然後編譯器就不需要合成它)。</span><span class="sxs-lookup"><span data-stu-id="9b07a-110">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="9b07a-111">因為這個屬性，執行階段會拒絕載入參考組件以供執行 (但仍可載入僅限反映模式)。</span><span class="sxs-lookup"><span data-stu-id="9b07a-111">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="9b07a-112">在組件上反映的工具需要確保它們載入的組件為僅限反映，否則就會從執行階段收到類型載入錯誤。</span><span class="sxs-lookup"><span data-stu-id="9b07a-112">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="9b07a-113">參考組件會進一步移除來自僅中繼資料組件的中繼資料 (私用成員)：</span><span class="sxs-lookup"><span data-stu-id="9b07a-113">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="9b07a-114">參考組件只有在 API 介面中所需項目的參考。</span><span class="sxs-lookup"><span data-stu-id="9b07a-114">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="9b07a-115">實際的組件可能有與特定實作相關的其他參考。</span><span class="sxs-lookup"><span data-stu-id="9b07a-115">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="9b07a-116">例如，`class C { private void M() { dynamic d = 1; ... } }` 的參考組件不參考 `dynamic` 所需的任何類型。</span><span class="sxs-lookup"><span data-stu-id="9b07a-116">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="9b07a-117">如果移除它們不會明顯影響編譯的話，則會移除私用函式的成員 (方法、屬性和事件)。</span><span class="sxs-lookup"><span data-stu-id="9b07a-117">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="9b07a-118">如果沒有任何 `InternalsVisibleTo` 屬性，請對內部函式成員執行相同的作業。</span><span class="sxs-lookup"><span data-stu-id="9b07a-118">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="9b07a-119">但所有類型 (包括私用或巢狀類型) 都會保留在參考組件中。</span><span class="sxs-lookup"><span data-stu-id="9b07a-119">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="9b07a-120">所有屬性都保留 (即使是內部屬性)。</span><span class="sxs-lookup"><span data-stu-id="9b07a-120">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="9b07a-121">所有虛擬方法都保留。</span><span class="sxs-lookup"><span data-stu-id="9b07a-121">All virtual methods are kept.</span></span> <span data-ttu-id="9b07a-122">保留明確的介面實作。</span><span class="sxs-lookup"><span data-stu-id="9b07a-122">Explicit interface implementations are kept.</span></span> <span data-ttu-id="9b07a-123">保留明確實作的屬性和事件，因為它們的存取子都是虛擬的 (因此保留)。</span><span class="sxs-lookup"><span data-stu-id="9b07a-123">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="9b07a-124">所有結構欄位都保留。</span><span class="sxs-lookup"><span data-stu-id="9b07a-124">All fields of a struct are kept.</span></span> <span data-ttu-id="9b07a-125">(這是 post-C#-7.1 細分的候選項目)</span><span class="sxs-lookup"><span data-stu-id="9b07a-125">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="9b07a-126">`-refonly` 和 [`-refout`](refout-compiler-option.md) 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="9b07a-126">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b07a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b07a-127">See also</span></span>
 [<span data-ttu-id="9b07a-128">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="9b07a-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="9b07a-129">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="9b07a-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
