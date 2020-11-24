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
ms.openlocfilehash: 337c4fd091ebf7c39f7eee2358ca4f4df239cce3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687524"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="716ce-102">ICorProfilerInfo::GetILFunctionBody 方法</span><span class="sxs-lookup"><span data-stu-id="716ce-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>

<span data-ttu-id="716ce-103">從標頭開始，取得 Microsoft 中繼語言 (MSIL 的方法主體指標) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="716ce-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="716ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="716ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="716ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="716ce-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="716ce-106">在函數所在之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="716ce-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="716ce-107">在方法的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="716ce-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="716ce-108">擴展方法標頭的指標。</span><span class="sxs-lookup"><span data-stu-id="716ce-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="716ce-109">擴展指定方法大小的整數。</span><span class="sxs-lookup"><span data-stu-id="716ce-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="716ce-110">備註</span><span class="sxs-lookup"><span data-stu-id="716ce-110">Remarks</span></span>  

 <span data-ttu-id="716ce-111">方法的範圍是它所在的模組。</span><span class="sxs-lookup"><span data-stu-id="716ce-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="716ce-112">因為 `GetILFunctionBody` 方法是設計為在 common language runtime (CLR) 載入 MSIL 程式碼之前，提供工具的存取權，所以它會使用方法的中繼資料 token 來尋找所需的實例。</span><span class="sxs-lookup"><span data-stu-id="716ce-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="716ce-113">`GetILFunctionBody` 如果 `methodId` 指向沒有任何 MSIL 程式碼 (的方法（例如抽象方法），或平台叫用 (PInvoke) 方法) ，則可以傳回 CORPROF_E_FUNCTION_NOT_IL HRESULT。</span><span class="sxs-lookup"><span data-stu-id="716ce-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="716ce-114">需求</span><span class="sxs-lookup"><span data-stu-id="716ce-114">Requirements</span></span>  

 <span data-ttu-id="716ce-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="716ce-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="716ce-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="716ce-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="716ce-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="716ce-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="716ce-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="716ce-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="716ce-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="716ce-119">See also</span></span>

- [<span data-ttu-id="716ce-120">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="716ce-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
