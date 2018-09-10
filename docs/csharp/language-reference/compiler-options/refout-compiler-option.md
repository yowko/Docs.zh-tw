---
title: -refout (C# 編譯器選項)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: e204a053f6f68a4b848d22c95c98f04edff58716
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506621"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="32d2d-102">-refout (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="32d2d-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="32d2d-103">**-refout** 選項指定參考組件應該輸出的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="32d2d-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="32d2d-104">這在發出 API 中會轉譯成 `metadataPeStream`。</span><span class="sxs-lookup"><span data-stu-id="32d2d-104">This translates to `metadataPeStream` in the Emit API.</span></span>

## <a name="syntax"></a><span data-ttu-id="32d2d-105">語法</span><span class="sxs-lookup"><span data-stu-id="32d2d-105">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="32d2d-106">引數</span><span class="sxs-lookup"><span data-stu-id="32d2d-106">Arguments</span></span>

 <span data-ttu-id="32d2d-107">`filepath` 參考組件的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="32d2d-107">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="32d2d-108">它通常應該符合主要組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="32d2d-108">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="32d2d-109">建議慣例 (由 MSBuild 使用) 是將參考組件放在相對於主要組件的 "ref/" 子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="32d2d-109">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="32d2d-110">備註</span><span class="sxs-lookup"><span data-stu-id="32d2d-110">Remarks</span></span>

<span data-ttu-id="32d2d-111">僅中繼資料組件以單一的 `throw null` 主體取代其方法主體，但包含匿名型別以外的所有成員。</span><span class="sxs-lookup"><span data-stu-id="32d2d-111">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="32d2d-112">使用 `throw null` 主體的原因 (相對於沒有主體)，是這樣 PEVerify 便可執行和傳遞 (因此驗證中繼資料的完整性)。</span><span class="sxs-lookup"><span data-stu-id="32d2d-112">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="32d2d-113">參考組件包含組件層級的 `ReferenceAssembly` 屬性。</span><span class="sxs-lookup"><span data-stu-id="32d2d-113">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="32d2d-114">這個屬性可在來源中指定 (然後編譯器就不需要合成它)。</span><span class="sxs-lookup"><span data-stu-id="32d2d-114">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="32d2d-115">因為這個屬性，執行階段會拒絕載入參考組件以供執行 (但仍可載入僅限反映模式)。</span><span class="sxs-lookup"><span data-stu-id="32d2d-115">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="32d2d-116">在組件上反映的工具需要確保它們載入的組件為僅限反映，否則就會從執行階段收到類型載入錯誤。</span><span class="sxs-lookup"><span data-stu-id="32d2d-116">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="32d2d-117">參考組件會進一步移除來自僅中繼資料組件的中繼資料 (私用成員)：</span><span class="sxs-lookup"><span data-stu-id="32d2d-117">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="32d2d-118">參考組件只有在 API 介面中所需項目的參考。</span><span class="sxs-lookup"><span data-stu-id="32d2d-118">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="32d2d-119">實際的組件可能有與特定實作相關的其他參考。</span><span class="sxs-lookup"><span data-stu-id="32d2d-119">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="32d2d-120">例如，`class C { private void M() { dynamic d = 1; ... } }` 的參考組件不參考 `dynamic` 所需的任何類型。</span><span class="sxs-lookup"><span data-stu-id="32d2d-120">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="32d2d-121">如果移除它們不會明顯影響編譯的話，則會移除私用函式的成員 (方法、屬性和事件)。</span><span class="sxs-lookup"><span data-stu-id="32d2d-121">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="32d2d-122">如果沒有任何 `InternalsVisibleTo` 屬性，請對內部函式成員執行相同的作業。</span><span class="sxs-lookup"><span data-stu-id="32d2d-122">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="32d2d-123">但所有類型 (包括私用或巢狀類型) 都會保留在參考組件中。</span><span class="sxs-lookup"><span data-stu-id="32d2d-123">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="32d2d-124">所有屬性都保留 (即使是內部屬性)。</span><span class="sxs-lookup"><span data-stu-id="32d2d-124">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="32d2d-125">所有虛擬方法都保留。</span><span class="sxs-lookup"><span data-stu-id="32d2d-125">All virtual methods are kept.</span></span> <span data-ttu-id="32d2d-126">保留明確的介面實作。</span><span class="sxs-lookup"><span data-stu-id="32d2d-126">Explicit interface implementations are kept.</span></span> <span data-ttu-id="32d2d-127">保留明確實作的屬性和事件，因為它們的存取子都是虛擬的 (因此保留)。</span><span class="sxs-lookup"><span data-stu-id="32d2d-127">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="32d2d-128">所有結構欄位都保留。</span><span class="sxs-lookup"><span data-stu-id="32d2d-128">All fields of a struct are kept.</span></span> <span data-ttu-id="32d2d-129">(這是 post-C#-7.1 細分的候選項目)</span><span class="sxs-lookup"><span data-stu-id="32d2d-129">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="32d2d-130">`-refout` 和 [`-refonly`](refonly-compiler-option.md) 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="32d2d-130">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="32d2d-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="32d2d-131">See Also</span></span>

- [<span data-ttu-id="32d2d-132">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="32d2d-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="32d2d-133">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="32d2d-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
