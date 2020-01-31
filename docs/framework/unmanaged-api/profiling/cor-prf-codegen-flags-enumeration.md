---
title: COR_PRF_CODEGEN_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
ms.openlocfilehash: 4dd4e39c9092d018f13e3bd2822e9492d71141ad
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867291"
---
# <a name="cor_prf_codegen_flags-enumeration"></a><span data-ttu-id="486a5-102">COR_PRF_CODEGEN_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="486a5-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="486a5-103">定義可使用[ICorProfilerFunctionControl：： SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md)方法設定的程式碼產生旗標。</span><span class="sxs-lookup"><span data-stu-id="486a5-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="486a5-104">語法</span><span class="sxs-lookup"><span data-stu-id="486a5-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="486a5-105">Members</span><span class="sxs-lookup"><span data-stu-id="486a5-105">Members</span></span>  
  
|<span data-ttu-id="486a5-106">成員</span><span class="sxs-lookup"><span data-stu-id="486a5-106">Member</span></span>|<span data-ttu-id="486a5-107">描述</span><span class="sxs-lookup"><span data-stu-id="486a5-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="486a5-108">不會將任何函式內嵌到這個函式的主體中。</span><span class="sxs-lookup"><span data-stu-id="486a5-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="486a5-109">不過，函式本身可能會內嵌至其呼叫端。</span><span class="sxs-lookup"><span data-stu-id="486a5-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="486a5-110">此函式的主體將會停用所有優化。</span><span class="sxs-lookup"><span data-stu-id="486a5-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="486a5-111">不過，函式本身可能仍會內嵌至其呼叫端。</span><span class="sxs-lookup"><span data-stu-id="486a5-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="486a5-112">備註</span><span class="sxs-lookup"><span data-stu-id="486a5-112">Remarks</span></span>  
 <span data-ttu-id="486a5-113">[ICorProfilerFunctionControl：： SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md)方法會使用 `COR_PRF_CODEGEN_FLAGS` 列舉，讓分析工具可以控制 JIT 重新編譯函式的程式碼產生。</span><span class="sxs-lookup"><span data-stu-id="486a5-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="486a5-114">需求</span><span class="sxs-lookup"><span data-stu-id="486a5-114">Requirements</span></span>  
 <span data-ttu-id="486a5-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="486a5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="486a5-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="486a5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="486a5-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="486a5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="486a5-118">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="486a5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="486a5-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="486a5-119">See also</span></span>

- [<span data-ttu-id="486a5-120">分析列舉</span><span class="sxs-lookup"><span data-stu-id="486a5-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
