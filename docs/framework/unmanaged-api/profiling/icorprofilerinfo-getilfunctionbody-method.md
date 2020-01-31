---
title: ICorProfilerInfo::GetILFunctionBody 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
ms.openlocfilehash: 8160bb5b9ca5e0a4e22a1a831e978eaf125e7605
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870488"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="45f4d-102">ICorProfilerInfo::GetILFunctionBody 方法</span><span class="sxs-lookup"><span data-stu-id="45f4d-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="45f4d-103">從標頭開始，取得 Microsoft 中繼語言（MSIL）程式碼中方法主體的指標。</span><span class="sxs-lookup"><span data-stu-id="45f4d-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45f4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="45f4d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45f4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="45f4d-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="45f4d-106">在函數所在模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="45f4d-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="45f4d-107">在方法的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="45f4d-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="45f4d-108">脫銷方法標頭的指標。</span><span class="sxs-lookup"><span data-stu-id="45f4d-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="45f4d-109">脫銷指定方法大小的整數。</span><span class="sxs-lookup"><span data-stu-id="45f4d-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45f4d-110">備註</span><span class="sxs-lookup"><span data-stu-id="45f4d-110">Remarks</span></span>  
 <span data-ttu-id="45f4d-111">方法是由其所在的模組限定範圍。</span><span class="sxs-lookup"><span data-stu-id="45f4d-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="45f4d-112">由於 `GetILFunctionBody` 方法是設計用來在 common language runtime （CLR）載入 MSIL 程式碼之前，先對其授與工具的存取權，因此它會使用方法的元資料標記來尋找所需的實例。</span><span class="sxs-lookup"><span data-stu-id="45f4d-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="45f4d-113">如果 `methodId` 指向不含任何 MSIL 程式碼的方法（例如抽象方法或平台叫用（PInvoke）方法），則 `GetILFunctionBody` 可以傳回 CORPROF_E_FUNCTION_NOT_IL HRESULT。</span><span class="sxs-lookup"><span data-stu-id="45f4d-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45f4d-114">需求</span><span class="sxs-lookup"><span data-stu-id="45f4d-114">Requirements</span></span>  
 <span data-ttu-id="45f4d-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="45f4d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45f4d-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45f4d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45f4d-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45f4d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45f4d-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45f4d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45f4d-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="45f4d-119">See also</span></span>

- [<span data-ttu-id="45f4d-120">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="45f4d-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
