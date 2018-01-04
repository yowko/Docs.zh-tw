---
title: "ICorProfilerInfo::GetILFunctionBody 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 035c2a1926d80b4aaea57523b4ecdd3da6873efe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="3c8fb-102">ICorProfilerInfo::GetILFunctionBody 方法</span><span class="sxs-lookup"><span data-stu-id="3c8fb-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="3c8fb-103">取得 Microsoft intermediate language (MSIL) 程式碼中，開始標頭在方法主體的指標。</span><span class="sxs-lookup"><span data-stu-id="3c8fb-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c8fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c8fb-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c8fb-105">參數</span><span class="sxs-lookup"><span data-stu-id="3c8fb-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="3c8fb-106">[in]此函式所在模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3c8fb-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="3c8fb-107">[in]方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3c8fb-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="3c8fb-108">[out]方法的標頭的指標。</span><span class="sxs-lookup"><span data-stu-id="3c8fb-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="3c8fb-109">[out]整數，指定方法的大小。</span><span class="sxs-lookup"><span data-stu-id="3c8fb-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c8fb-110">備註</span><span class="sxs-lookup"><span data-stu-id="3c8fb-110">Remarks</span></span>  
 <span data-ttu-id="3c8fb-111">方法的範圍是由其所在的模組。</span><span class="sxs-lookup"><span data-stu-id="3c8fb-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="3c8fb-112">因為`GetILFunctionBody`方法設計用來讓工具可以存取的 MSIL 程式碼之前已載入 common language runtime (CLR)，它使用的中繼資料語彙基元的方法來尋找所需的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3c8fb-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="3c8fb-113">`GetILFunctionBody`如果可以傳回 CORPROF_E_FUNCTION_NOT_IL HRESULT`methodId`指向方法沒有任何 MSIL 程式碼 （例如，一個抽象方法或平台叫用 (PInvoke) 方法）。</span><span class="sxs-lookup"><span data-stu-id="3c8fb-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c8fb-114">需求</span><span class="sxs-lookup"><span data-stu-id="3c8fb-114">Requirements</span></span>  
 <span data-ttu-id="3c8fb-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c8fb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c8fb-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3c8fb-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c8fb-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c8fb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c8fb-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c8fb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c8fb-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c8fb-119">See Also</span></span>  
 [<span data-ttu-id="3c8fb-120">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="3c8fb-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
