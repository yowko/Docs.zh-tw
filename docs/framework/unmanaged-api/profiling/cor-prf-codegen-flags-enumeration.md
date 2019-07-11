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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 190774b17d6e8214dd2358edb74f3eaf3b079fc2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782665"
---
# <a name="corprfcodegenflags-enumeration"></a><span data-ttu-id="232e7-102">COR_PRF_CODEGEN_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="232e7-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="232e7-103">定義可以使用設定的程式碼產生旗標[icorprofilerfunctioncontrol:: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="232e7-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="232e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="232e7-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="232e7-105">成員</span><span class="sxs-lookup"><span data-stu-id="232e7-105">Members</span></span>  
  
|<span data-ttu-id="232e7-106">成員</span><span class="sxs-lookup"><span data-stu-id="232e7-106">Member</span></span>|<span data-ttu-id="232e7-107">描述</span><span class="sxs-lookup"><span data-stu-id="232e7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="232e7-108">沒有任何函式會內嵌於此函式主體。</span><span class="sxs-lookup"><span data-stu-id="232e7-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="232e7-109">不過，您可能會內嵌至其呼叫端函式本身。</span><span class="sxs-lookup"><span data-stu-id="232e7-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="232e7-110">將停用此函式主體的所有最佳化項目。</span><span class="sxs-lookup"><span data-stu-id="232e7-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="232e7-111">不過，函式本身仍可能會內嵌至其呼叫者。</span><span class="sxs-lookup"><span data-stu-id="232e7-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="232e7-112">備註</span><span class="sxs-lookup"><span data-stu-id="232e7-112">Remarks</span></span>  
 <span data-ttu-id="232e7-113">`COR_PRF_CODEGEN_FLAGS`列舉由[icorprofilerfunctioncontrol:: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)方法來啟用分析工具，來控制 JIT 重新編譯函式的程式碼產生。</span><span class="sxs-lookup"><span data-stu-id="232e7-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="232e7-114">需求</span><span class="sxs-lookup"><span data-stu-id="232e7-114">Requirements</span></span>  
 <span data-ttu-id="232e7-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="232e7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="232e7-116">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="232e7-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="232e7-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="232e7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="232e7-118">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="232e7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="232e7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="232e7-119">See also</span></span>

- [<span data-ttu-id="232e7-120">分析列舉</span><span class="sxs-lookup"><span data-stu-id="232e7-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
