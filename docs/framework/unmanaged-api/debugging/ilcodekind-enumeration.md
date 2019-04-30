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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f7e20618180961ab6d8ad0bbb79a626a4a7f4f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993471"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="e9f3e-102">ILCodeKind 列舉</span><span class="sxs-lookup"><span data-stu-id="e9f3e-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="e9f3e-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="e9f3e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e9f3e-104">提供值，指定偵錯工具是否能夠存取分析工具 ReJIT 檢測中加入的區域變數或程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9f3e-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9f3e-105">語法</span><span class="sxs-lookup"><span data-stu-id="e9f3e-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="e9f3e-106">成員</span><span class="sxs-lookup"><span data-stu-id="e9f3e-106">Members</span></span>  
  
|<span data-ttu-id="e9f3e-107">成員名稱</span><span class="sxs-lookup"><span data-stu-id="e9f3e-107">Member name</span></span>|<span data-ttu-id="e9f3e-108">描述</span><span class="sxs-lookup"><span data-stu-id="e9f3e-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="e9f3e-109">偵錯工具無權存取 ReJIT 檢測的資訊。</span><span class="sxs-lookup"><span data-stu-id="e9f3e-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="e9f3e-110">偵錯工具有權存取 ReJIT 檢測的資訊。</span><span class="sxs-lookup"><span data-stu-id="e9f3e-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9f3e-111">備註</span><span class="sxs-lookup"><span data-stu-id="e9f3e-111">Remarks</span></span>  
 <span data-ttu-id="e9f3e-112">成員`ILCodeKind`列舉型別可以傳遞至[EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)並[GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)方法，以決定偵錯工具是否可存取加入分析工具中的變數Rejit 測試設備，以及[GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)方法，以判斷是否可以存取偵錯工具已檢測的 IL。</span><span class="sxs-lookup"><span data-stu-id="e9f3e-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9f3e-113">需求</span><span class="sxs-lookup"><span data-stu-id="e9f3e-113">Requirements</span></span>  
 <span data-ttu-id="e9f3e-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f3e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9f3e-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9f3e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9f3e-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9f3e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9f3e-117">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9f3e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f3e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9f3e-118">See also</span></span>

- [<span data-ttu-id="e9f3e-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="e9f3e-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="e9f3e-120">ICorDebugILFrame4 介面</span><span class="sxs-lookup"><span data-stu-id="e9f3e-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="e9f3e-121">ReJIT:操作說明指南</span><span class="sxs-lookup"><span data-stu-id="e9f3e-121">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
