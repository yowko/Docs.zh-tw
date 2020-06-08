---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 8ed3f305deceacb976aeff994db1588f9e1ce1fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495524"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="ddd5b-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法</span><span class="sxs-lookup"><span data-stu-id="ddd5b-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="ddd5b-103">傳回指定之 NGen 模組中所定義之所有方法的列舉值，並內嵌指定的方法。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-103">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="ddd5b-104">語法</span><span class="sxs-lookup"><span data-stu-id="ddd5b-104">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="ddd5b-105">參數</span><span class="sxs-lookup"><span data-stu-id="ddd5b-105">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="ddd5b-106">在NGen 模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-106">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="ddd5b-107">在定義之模組的識別碼 `inlineeMethodId` 。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-107">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="ddd5b-108">如需詳細資訊，請參閱「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-108">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="ddd5b-109">在內嵌方法的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-109">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="ddd5b-110">如需詳細資訊，請參閱「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-110">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="ddd5b-111">脫銷表示是否 `ppEnum` 包含所有方法內嵌指定方法的旗標。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-111">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="ddd5b-112">如需詳細資訊，請參閱「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-112">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="ddd5b-113">脫銷列舉值的位址指標</span><span class="sxs-lookup"><span data-stu-id="ddd5b-113">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="ddd5b-114">備註</span><span class="sxs-lookup"><span data-stu-id="ddd5b-114">Remarks</span></span>

<span data-ttu-id="ddd5b-115">`inlineeModuleId`和 `inlineeMethodId` 會構成可能內嵌之方法的完整識別碼。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-115">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="ddd5b-116">例如，假設模組 `A` 定義了方法 `Simple.Add` ：</span><span class="sxs-lookup"><span data-stu-id="ddd5b-116">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="ddd5b-117">和模組 B 定義 `Fancy.AddTwice` ：</span><span class="sxs-lookup"><span data-stu-id="ddd5b-117">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="ddd5b-118">讓也假設 `Fancy.AddTwice` 內嵌呼叫 `SimpleAdd` 。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-118">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="ddd5b-119">分析工具可以使用這個列舉值來尋找模組 B 中定義的所有方法（內嵌 `Simple.Add` ），而結果會列舉 `AddTwice` 。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-119">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="ddd5b-120">`inlineeModuleId`是模組的識別碼 `A` ，而 `inlineeMethodId` 是的識別碼 `Simple.Add(int a, int b)` 。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-120">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="ddd5b-121">如果在函式傳回 `incompleteData` 之後為 true，列舉值就不會包含內嵌指定方法的所有方法。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-121">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="ddd5b-122">當 inliners 模組的一或多個直接或間接相依性尚未載入時，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-122">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="ddd5b-123">如果分析工具需要精確的資料，當載入更多模組時，最好是在每個模組載入時重試。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-123">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="ddd5b-124">`EnumNgenModuleMethodsInliningThisMethod`方法可以用來解決 ReJIT 內嵌的限制。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-124">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="ddd5b-125">ReJIT 可讓分析工具變更方法的執行，然後立即為其建立新程式碼。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-125">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="ddd5b-126">例如，我們可以變更 `Simple.Add` 如下：</span><span class="sxs-lookup"><span data-stu-id="ddd5b-126">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="ddd5b-127">不過，因為已經 `Fancy.AddTwice` 內嵌 `Simple.Add` ，所以它會繼續具有與之前相同的行為。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-127">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="ddd5b-128">若要解決這項限制，呼叫者必須在所有模組中搜尋所有方法，以內嵌 `Simple.Add` 和使用 `ICorProfilerInfo5::RequestRejit` 這些方法。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-128">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="ddd5b-129">重新編譯方法時，會有新的行為， `Simple.Add` 而不是舊的行為。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-129">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="ddd5b-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="ddd5b-130">Requirements</span></span>

<span data-ttu-id="ddd5b-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ddd5b-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ddd5b-132">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ddd5b-132">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="ddd5b-133">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddd5b-133">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ddd5b-134">**.NET Framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddd5b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ddd5b-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddd5b-135">See also</span></span>

- [<span data-ttu-id="ddd5b-136">ICorProfilerInfo6 介面</span><span class="sxs-lookup"><span data-stu-id="ddd5b-136">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)
