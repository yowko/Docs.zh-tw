---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07b1c905e587708336ce690bbf3d187b2d21e5b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568149"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="d3118-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法</span><span class="sxs-lookup"><span data-stu-id="d3118-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>
<span data-ttu-id="d3118-103">[.NET Framework 4.6 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="d3118-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="d3118-104">傳回列舉值，指定的 NGen 模組和內嵌指定的方法中所定義的所有方法。</span><span class="sxs-lookup"><span data-stu-id="d3118-104">Returns an enumerator to all the methods that          are defined in  a given NGen module and          inline a given method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3118-105">語法</span><span class="sxs-lookup"><span data-stu-id="d3118-105">Syntax</span></span>  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3118-106">參數</span><span class="sxs-lookup"><span data-stu-id="d3118-106">Parameters</span></span>  
 `inlinersModuleId`  
 <span data-ttu-id="d3118-107">[in]NGen 模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d3118-107">[in] The identifier of an NGen module.</span></span>  
  
 `inlineeModuleId`  
 <span data-ttu-id="d3118-108">[in]模組中定義的識別項`inlineeMethodId`。</span><span class="sxs-lookup"><span data-stu-id="d3118-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="d3118-109">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="d3118-109">See the Remarks section for more information.</span></span>  
  
 `inlineeMethodId`  
 <span data-ttu-id="d3118-110">[in]內嵌方法的識別項。</span><span class="sxs-lookup"><span data-stu-id="d3118-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="d3118-111">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="d3118-111">See the Remarks section for more information.</span></span>  
  
 `incompleteData`  
 <span data-ttu-id="d3118-112">[out]旗標，指出是否`ppEnum`包含內嵌的所有方法指定的方法。</span><span class="sxs-lookup"><span data-stu-id="d3118-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="d3118-113">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="d3118-113">See the Remarks section for more information.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="d3118-114">[out]列舉值的位址指標</span><span class="sxs-lookup"><span data-stu-id="d3118-114">[out] A pointer to the address of an enumerator</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3118-115">備註</span><span class="sxs-lookup"><span data-stu-id="d3118-115">Remarks</span></span>  
 <span data-ttu-id="d3118-116">`inlineeModuleId` 和`inlineeMethodId`構成可能內嵌方法的完整識別碼。</span><span class="sxs-lookup"><span data-stu-id="d3118-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="d3118-117">例如，假設模組`A`定義的方法`Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="d3118-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 <span data-ttu-id="d3118-118">和模組 Bdefines `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="d3118-118">and module Bdefines `Fancy.AddTwice`:</span></span>  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 <span data-ttu-id="d3118-119">我們也假設所`Fancy.AddTwice`內嵌呼叫至`SimpleAdd`。</span><span class="sxs-lookup"><span data-stu-id="d3118-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="d3118-120">分析工具可以使用這個列舉值，來尋找模組 B 中定義的所有方法的內嵌`Simple.Add`，並會在列舉結果`AddTwice`。</span><span class="sxs-lookup"><span data-stu-id="d3118-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="d3118-121">`inlineeModuleId` 是模組的識別項`A`，並`inlineeeMethodId`是識別碼`Simple.Add(int a, int b)`。</span><span class="sxs-lookup"><span data-stu-id="d3118-121">`inlineeModuleId` is the identifier of module `A`,   and `inlineeeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>  
  
 <span data-ttu-id="d3118-122">如果`incompleteData`成立的函式之後傳回列舉值不包含內嵌的所有方法指定的方法。</span><span class="sxs-lookup"><span data-stu-id="d3118-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="d3118-123">這種情形時，或您尚未尚未載入 inliners 模組的更直接或間接的相依性。</span><span class="sxs-lookup"><span data-stu-id="d3118-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="d3118-124">如果程式碼剖析工具需要正確資料時，它應該稍後重試多個模組載入時，最好是在每個模組載入。</span><span class="sxs-lookup"><span data-stu-id="d3118-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>  
  
 <span data-ttu-id="d3118-125">`EnumNgenModuleMethodsInliningThisMethod`方法可用來解決限制上內嵌的 ReJIT。</span><span class="sxs-lookup"><span data-stu-id="d3118-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="d3118-126">ReJIT 可讓您變更方法的實作，然後在即時的建立新的程式碼分析工具。</span><span class="sxs-lookup"><span data-stu-id="d3118-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="d3118-127">比方說，我們無法變更`Simple.Add`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3118-127">For example, we could change `Simple.Add` as follows:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 <span data-ttu-id="d3118-128">不過由於`Fancy.AddTwice`具有已內嵌`Simple.Add`，它會繼續如往常有相同的行為。</span><span class="sxs-lookup"><span data-stu-id="d3118-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="d3118-129">若要解決這項限制，呼叫端具有所有方法的所有模組中內嵌的搜尋`Simple.Add`並用`ICorProfilerInfo5::RequestRejit`上每個這些方法。</span><span class="sxs-lookup"><span data-stu-id="d3118-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="d3118-130">重新編譯方法時，它們會有的新行為`Simple.Add`而不是舊的行為。</span><span class="sxs-lookup"><span data-stu-id="d3118-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3118-131">需求</span><span class="sxs-lookup"><span data-stu-id="d3118-131">Requirements</span></span>  
 <span data-ttu-id="d3118-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3118-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3118-133">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d3118-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3118-134">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3118-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3118-135">**.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3118-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3118-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3118-136">See also</span></span>
- [<span data-ttu-id="d3118-137">ICorProfilerInfo6 介面</span><span class="sxs-lookup"><span data-stu-id="d3118-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
