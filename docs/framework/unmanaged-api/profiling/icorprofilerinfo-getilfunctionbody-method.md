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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b2960bc0cfc39adb9b7cbca236d495baf630a173
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991844"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="a5fa0-102">ICorProfilerInfo::GetILFunctionBody 方法</span><span class="sxs-lookup"><span data-stu-id="a5fa0-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="a5fa0-103">Microsoft intermediate language (MSIL) 程式碼，開始標頭中取得方法主體的指標。</span><span class="sxs-lookup"><span data-stu-id="a5fa0-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5fa0-104">語法</span><span class="sxs-lookup"><span data-stu-id="a5fa0-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5fa0-105">參數</span><span class="sxs-lookup"><span data-stu-id="a5fa0-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="a5fa0-106">[in]函數所在之模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="a5fa0-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="a5fa0-107">[in]方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a5fa0-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="a5fa0-108">[out]方法的標頭指標。</span><span class="sxs-lookup"><span data-stu-id="a5fa0-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="a5fa0-109">[out]整數，指定方法的大小。</span><span class="sxs-lookup"><span data-stu-id="a5fa0-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5fa0-110">備註</span><span class="sxs-lookup"><span data-stu-id="a5fa0-110">Remarks</span></span>  
 <span data-ttu-id="a5fa0-111">方法的範圍是由其所在的模組。</span><span class="sxs-lookup"><span data-stu-id="a5fa0-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="a5fa0-112">因為`GetILFunctionBody`方法設計用來讓 MSIL 程式碼的工具存取之前已經將它載入 common language runtime (CLR)，它使用的中繼資料語彙基元的方法來尋找所需的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a5fa0-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="a5fa0-113">`GetILFunctionBody` 如果可以傳回 CORPROF_E_FUNCTION_NOT_IL HRESULT`methodId`指向一個方法，沒有任何 MSIL 程式碼 （例如抽象方法或平台叫用 (PInvoke) 方法）。</span><span class="sxs-lookup"><span data-stu-id="a5fa0-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5fa0-114">需求</span><span class="sxs-lookup"><span data-stu-id="a5fa0-114">Requirements</span></span>  
 <span data-ttu-id="a5fa0-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5fa0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5fa0-116">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a5fa0-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5fa0-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5fa0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5fa0-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5fa0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5fa0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5fa0-119">See also</span></span>

- [<span data-ttu-id="a5fa0-120">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="a5fa0-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
