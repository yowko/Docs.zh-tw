---
title: "ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6cf0bccebbfe5620ef329cc8c6f72582a7afe85a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="15219-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法</span><span class="sxs-lookup"><span data-stu-id="15219-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>
<span data-ttu-id="15219-103">[在.NET Framework 4.6 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="15219-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="15219-104">提供的 NGen 模組和內嵌指定的方法中所定義的所有方法傳回的列舉值。</span><span class="sxs-lookup"><span data-stu-id="15219-104">Returns an enumerator to all the methods that          are defined in  a given NGen module and          inline a given method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15219-105">語法</span><span class="sxs-lookup"><span data-stu-id="15219-105">Syntax</span></span>  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15219-106">參數</span><span class="sxs-lookup"><span data-stu-id="15219-106">Parameters</span></span>  
 `inlinersModuleId`  
 <span data-ttu-id="15219-107">[in]NGen 模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="15219-107">[in] The identifier of an NGen module.</span></span>  
  
 `inlineeModuleId`  
 <span data-ttu-id="15219-108">[in]定義模組的識別碼`inlineeMethodId`。</span><span class="sxs-lookup"><span data-stu-id="15219-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="15219-109">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="15219-109">See the Remarks section for more information.</span></span>  
  
 `inlineeMethodId`  
 <span data-ttu-id="15219-110">[in]內嵌的方法識別項。</span><span class="sxs-lookup"><span data-stu-id="15219-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="15219-111">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="15219-111">See the Remarks section for more information.</span></span>  
  
 `incompleteData`  
 <span data-ttu-id="15219-112">[out]旗標，指出是否`ppEnum`包含內嵌的所有方法指定的方法。</span><span class="sxs-lookup"><span data-stu-id="15219-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="15219-113">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="15219-113">See the Remarks section for more information.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="15219-114">[out]列舉值的位址指標</span><span class="sxs-lookup"><span data-stu-id="15219-114">[out] A pointer to the address of an enumerator</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15219-115">備註</span><span class="sxs-lookup"><span data-stu-id="15219-115">Remarks</span></span>  
 <span data-ttu-id="15219-116">`inlineeModuleId`和`inlineeMethodId`結合在一起形成完整的識別項可能是內嵌的方法。</span><span class="sxs-lookup"><span data-stu-id="15219-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="15219-117">例如，假設模組`A`定義的方法`Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="15219-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 <span data-ttu-id="15219-118">和模組 Bdefines `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="15219-118">and module Bdefines `Fancy.AddTwice`:</span></span>  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 <span data-ttu-id="15219-119">我們也假設，`Fancy.AddTwice`內嵌呼叫至`SimpleAdd`。</span><span class="sxs-lookup"><span data-stu-id="15219-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="15219-120">分析工具可以使用這個列舉值，來尋找模組 B 中定義的所有方法的內嵌`Simple.Add`，並會列舉結果`AddTwice`。</span><span class="sxs-lookup"><span data-stu-id="15219-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="15219-121">`inlineeModuleId`為模組的識別碼`A`，和`inlineeeMethodId`識別`Simple.Add(int a, int b)`。</span><span class="sxs-lookup"><span data-stu-id="15219-121">`inlineeModuleId` is the identifier of module `A`,   and `inlineeeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>  
  
 <span data-ttu-id="15219-122">如果`incompleteData`成立的函式之後傳回列舉值不包含內嵌的所有方法指定的方法。</span><span class="sxs-lookup"><span data-stu-id="15219-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="15219-123">這種情形時，或尚未尚未載入的模組 inliners 更直接或間接的相依性。</span><span class="sxs-lookup"><span data-stu-id="15219-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="15219-124">如果分析工具需要正確資料時，它應該稍後重試多個模組載入時，最好是在每個模組載入。</span><span class="sxs-lookup"><span data-stu-id="15219-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>  
  
 <span data-ttu-id="15219-125">`EnumNgenModuleMethodsInliningThisMethod`方法可用來解決限制上內嵌的 ReJIT。</span><span class="sxs-lookup"><span data-stu-id="15219-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="15219-126">ReJIT 可讓您變更方法的實作，然後為其建立新的程式碼即時分析工具。</span><span class="sxs-lookup"><span data-stu-id="15219-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="15219-127">例如，我們可以變更`Simple.Add`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="15219-127">For example, we could change `Simple.Add` as follows:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 <span data-ttu-id="15219-128">但是因為`Fancy.AddTwice`具有已內嵌`Simple.Add`，它會繼續如往常一般有相同的行為。</span><span class="sxs-lookup"><span data-stu-id="15219-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="15219-129">若要解決這項限制，呼叫端必須搜尋所有方法中的所有模組的內嵌`Simple.Add`並用`ICorProfilerInfo5::RequestRejit`上每個這些方法。</span><span class="sxs-lookup"><span data-stu-id="15219-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="15219-130">重新編譯方法時，他們必須的新行為`Simple.Add`而不是舊的行為。</span><span class="sxs-lookup"><span data-stu-id="15219-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15219-131">需求</span><span class="sxs-lookup"><span data-stu-id="15219-131">Requirements</span></span>  
 <span data-ttu-id="15219-132">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15219-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15219-133">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="15219-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15219-134">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15219-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15219-135">**.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15219-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15219-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15219-136">See Also</span></span>  
 [<span data-ttu-id="15219-137">ICorProfilerInfo6 介面</span><span class="sxs-lookup"><span data-stu-id="15219-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
