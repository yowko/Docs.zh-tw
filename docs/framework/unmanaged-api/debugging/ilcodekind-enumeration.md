---
title: ILCodeKind 列舉
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: b59fbc2acefa907bb3f881b7ed183388d2e4c368
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103363"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="3a359-102">ILCodeKind 列舉</span><span class="sxs-lookup"><span data-stu-id="3a359-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="3a359-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="3a359-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3a359-104">提供值，指定偵錯工具是否能夠存取分析工具 ReJIT 檢測中加入的區域變數或程式碼。</span><span class="sxs-lookup"><span data-stu-id="3a359-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a359-105">語法</span><span class="sxs-lookup"><span data-stu-id="3a359-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="3a359-106">成員</span><span class="sxs-lookup"><span data-stu-id="3a359-106">Members</span></span>  
  
|<span data-ttu-id="3a359-107">成員名稱</span><span class="sxs-lookup"><span data-stu-id="3a359-107">Member name</span></span>|<span data-ttu-id="3a359-108">描述</span><span class="sxs-lookup"><span data-stu-id="3a359-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="3a359-109">偵錯工具無權存取 ReJIT 檢測的資訊。</span><span class="sxs-lookup"><span data-stu-id="3a359-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="3a359-110">偵錯工具有權存取 ReJIT 檢測的資訊。</span><span class="sxs-lookup"><span data-stu-id="3a359-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a359-111">備註</span><span class="sxs-lookup"><span data-stu-id="3a359-111">Remarks</span></span>  
 <span data-ttu-id="3a359-112">`ILCodeKind` 列舉的成員可以傳遞至[EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)和[GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)方法，以判斷偵錯工具是否可以存取在 Profiler ReJIT 檢測和 [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) 中新增的變數用來判斷偵錯工具是否可以存取已檢測 IL 的方法。</span><span class="sxs-lookup"><span data-stu-id="3a359-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a359-113">需求</span><span class="sxs-lookup"><span data-stu-id="3a359-113">Requirements</span></span>  
 <span data-ttu-id="3a359-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a359-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a359-115">**標頭：** Cordebug.h .idl，Cordebug.h。h</span><span class="sxs-lookup"><span data-stu-id="3a359-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a359-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a359-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a359-117">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a359-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a359-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a359-118">See also</span></span>

- [<span data-ttu-id="3a359-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="3a359-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="3a359-120">ICorDebugILFrame4 介面</span><span class="sxs-lookup"><span data-stu-id="3a359-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="3a359-121">ReJIT：使用說明指南</span><span class="sxs-lookup"><span data-stu-id="3a359-121">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
