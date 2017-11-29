---
title: "COR_PRF_CODEGEN_FLAGS 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_CODEGEN_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_CODEGEN_FLAGS
helpviewer_keywords: COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2c97510077fefd730827ac00326d267fd1c62ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corprfcodegenflags-enumeration"></a><span data-ttu-id="868f0-102">COR_PRF_CODEGEN_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="868f0-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="868f0-103">定義的程式碼產生旗標可以設定的[icorprofilerfunctioncontrol:: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="868f0-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="868f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="868f0-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="868f0-105">成員</span><span class="sxs-lookup"><span data-stu-id="868f0-105">Members</span></span>  
  
|<span data-ttu-id="868f0-106">成員</span><span class="sxs-lookup"><span data-stu-id="868f0-106">Member</span></span>|<span data-ttu-id="868f0-107">說明</span><span class="sxs-lookup"><span data-stu-id="868f0-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="868f0-108">沒有函式會內嵌於此函式主體。</span><span class="sxs-lookup"><span data-stu-id="868f0-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="868f0-109">不過，您可能會內嵌於其呼叫端函式本身。</span><span class="sxs-lookup"><span data-stu-id="868f0-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="868f0-110">此函式主體會停用所有的最佳化。</span><span class="sxs-lookup"><span data-stu-id="868f0-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="868f0-111">不過，函式本身可能仍在進行內嵌於其呼叫端。</span><span class="sxs-lookup"><span data-stu-id="868f0-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="868f0-112">備註</span><span class="sxs-lookup"><span data-stu-id="868f0-112">Remarks</span></span>  
 <span data-ttu-id="868f0-113">`COR_PRF_CODEGEN_FLAGS`項列舉供[icorprofilerfunctioncontrol:: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)方法，以啟用程式碼剖析工具，以控制 JIT 重新編譯函式的程式碼產生。</span><span class="sxs-lookup"><span data-stu-id="868f0-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="868f0-114">需求</span><span class="sxs-lookup"><span data-stu-id="868f0-114">Requirements</span></span>  
 <span data-ttu-id="868f0-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="868f0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="868f0-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="868f0-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="868f0-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="868f0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="868f0-118">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="868f0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="868f0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="868f0-119">See Also</span></span>  
 [<span data-ttu-id="868f0-120">分析列舉</span><span class="sxs-lookup"><span data-stu-id="868f0-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
