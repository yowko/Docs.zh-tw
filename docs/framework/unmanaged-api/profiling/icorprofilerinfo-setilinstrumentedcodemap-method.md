---
title: ICorProfilerInfo::SetILInstrumentedCodeMap 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a574a04e5746a8b2c9c32160e82aa503b392729
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792635"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="d477a-102">ICorProfilerInfo::SetILInstrumentedCodeMap 方法</span><span class="sxs-lookup"><span data-stu-id="d477a-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="d477a-103">設定使用指定的 Microsoft intermediate language (MSIL) 對應項目指定的函式的程式碼對應。</span><span class="sxs-lookup"><span data-stu-id="d477a-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d477a-104">在.NET Framework 2.0 版中，呼叫`SetILInstrumentedCodeMap`上`FunctionID`代表特定的應用程式定義域中的泛型函式會影響該函式應用程式定義域中的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="d477a-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d477a-105">語法</span><span class="sxs-lookup"><span data-stu-id="d477a-105">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d477a-106">參數</span><span class="sxs-lookup"><span data-stu-id="d477a-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d477a-107">[in]要設定 code map 函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d477a-107">[in] The ID of the function for which to set the code map.</span></span>  
  
 `fStartJit`  
 <span data-ttu-id="d477a-108">[in]布林值，指出是否在呼叫`SetILInstrumentedCodeMap`方法是為特定的第一個`FunctionID`。</span><span class="sxs-lookup"><span data-stu-id="d477a-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="d477a-109">設定`fStartJit`來`true`中的第一個呼叫`SetILInstrumentedCodeMap`針對給定`FunctionID`，以及`false`之後。</span><span class="sxs-lookup"><span data-stu-id="d477a-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>  
  
 `cILMapEntries`  
 <span data-ttu-id="d477a-110">[in]中的項目數`cILMapEntries`陣列。</span><span class="sxs-lookup"><span data-stu-id="d477a-110">[in] The number of elements in the `cILMapEntries` array.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="d477a-111">[in]COR_IL_MAP 結構陣列，其中每個指定的 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="d477a-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d477a-112">備註</span><span class="sxs-lookup"><span data-stu-id="d477a-112">Remarks</span></span>  
 <span data-ttu-id="d477a-113">分析工具通常會插入方法的原始程式碼中的陳述式以檢測方法 （例如，在達到指定的原始程式行時通知）。</span><span class="sxs-lookup"><span data-stu-id="d477a-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="d477a-114">`SetILInstrumentedCodeMap` 可讓分析工具將原始的 MSIL 指令對應至其新位置。</span><span class="sxs-lookup"><span data-stu-id="d477a-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="d477a-115">可以使用分析工具[icorprofilerinfo:: Getiltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)方法來取得原始的 MSIL 位移指定的原生位移。</span><span class="sxs-lookup"><span data-stu-id="d477a-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>  
  
 <span data-ttu-id="d477a-116">偵錯工具會假設每個舊位移是指原始、 未修改的 MSIL 程式碼中的 MSIL 位移，而每個新的位移是指在新的已檢測的程式碼的 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="d477a-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="d477a-117">此對應應該以遞增的順序排序。</span><span class="sxs-lookup"><span data-stu-id="d477a-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="d477a-118">逐步執行才能正常運作，請遵循這些指導方針：</span><span class="sxs-lookup"><span data-stu-id="d477a-118">For stepping to work properly, follow these guidelines:</span></span>  
  
- <span data-ttu-id="d477a-119">無法重新排序已檢測的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d477a-119">Do not reorder instrumented MSIL code.</span></span>  
  
- <span data-ttu-id="d477a-120">請勿移除原始的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d477a-120">Do not remove the original MSIL code.</span></span>  
  
- <span data-ttu-id="d477a-121">包含在對應中的程式資料庫 (PDB) 檔案中的所有序列點的項目。</span><span class="sxs-lookup"><span data-stu-id="d477a-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="d477a-122">對應不會插補遺漏的項目。</span><span class="sxs-lookup"><span data-stu-id="d477a-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="d477a-123">因此，假設下列對應：</span><span class="sxs-lookup"><span data-stu-id="d477a-123">So, given the following map:</span></span>  
  
     <span data-ttu-id="d477a-124">(0，0 新)</span><span class="sxs-lookup"><span data-stu-id="d477a-124">(0 old, 0 new)</span></span>  
  
     <span data-ttu-id="d477a-125">(5，-10 新)</span><span class="sxs-lookup"><span data-stu-id="d477a-125">(5 old, 10 new)</span></span>  
  
     <span data-ttu-id="d477a-126">(9，-20 新)</span><span class="sxs-lookup"><span data-stu-id="d477a-126">(9 old, 20 new)</span></span>  
  
    - <span data-ttu-id="d477a-127">0、 1、 2、 3 或 4 的舊位移會對應至新的位移 0。</span><span class="sxs-lookup"><span data-stu-id="d477a-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>  
  
    - <span data-ttu-id="d477a-128">5、 6、 7 或 8 的舊位移會對應至 10 的新位移。</span><span class="sxs-lookup"><span data-stu-id="d477a-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
    - <span data-ttu-id="d477a-129">9 或更新版本的舊位移會對應至新的位移 20。</span><span class="sxs-lookup"><span data-stu-id="d477a-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
    - <span data-ttu-id="d477a-130">0、 1、 2、 3、 4、 5、 6、 7、 8 或 9 新位移會對應至舊的位移 0。</span><span class="sxs-lookup"><span data-stu-id="d477a-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
    - <span data-ttu-id="d477a-131">新的位移，10、 11、 12、 13、 14、 15、 16、 17、 18 或 19 的會對應至舊位移 5。</span><span class="sxs-lookup"><span data-stu-id="d477a-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
    - <span data-ttu-id="d477a-132">20 或更高版本的新位移會對應至舊位移 9。</span><span class="sxs-lookup"><span data-stu-id="d477a-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d477a-133">需求</span><span class="sxs-lookup"><span data-stu-id="d477a-133">Requirements</span></span>  
 <span data-ttu-id="d477a-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d477a-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d477a-135">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d477a-135">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d477a-136">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d477a-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d477a-137">**.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d477a-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d477a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d477a-138">See also</span></span>

- [<span data-ttu-id="d477a-139">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="d477a-139">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
