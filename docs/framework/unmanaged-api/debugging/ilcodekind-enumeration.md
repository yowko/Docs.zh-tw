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
ms.openlocfilehash: b9d27c3e3cd42039aeefcb517ecc81eadeb5c183
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557420"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="5aac8-102">ILCodeKind 列舉</span><span class="sxs-lookup"><span data-stu-id="5aac8-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="5aac8-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="5aac8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5aac8-104">提供值，指定偵錯工具是否能夠存取分析工具 ReJIT 檢測中加入的區域變數或程式碼。</span><span class="sxs-lookup"><span data-stu-id="5aac8-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aac8-105">語法</span><span class="sxs-lookup"><span data-stu-id="5aac8-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="5aac8-106">成員</span><span class="sxs-lookup"><span data-stu-id="5aac8-106">Members</span></span>  
  
|<span data-ttu-id="5aac8-107">成員名稱</span><span class="sxs-lookup"><span data-stu-id="5aac8-107">Member name</span></span>|<span data-ttu-id="5aac8-108">描述</span><span class="sxs-lookup"><span data-stu-id="5aac8-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="5aac8-109">偵錯工具無權存取 ReJIT 檢測的資訊。</span><span class="sxs-lookup"><span data-stu-id="5aac8-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="5aac8-110">偵錯工具有權存取 ReJIT 檢測的資訊。</span><span class="sxs-lookup"><span data-stu-id="5aac8-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5aac8-111">備註</span><span class="sxs-lookup"><span data-stu-id="5aac8-111">Remarks</span></span>  
 <span data-ttu-id="5aac8-112">列舉的成員 `ILCodeKind` 可以傳遞至 [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) 和 [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) 方法，以判斷偵錯工具是否可以存取在 profiler ReJIT 檢測中加入的變數，以及至 [GetCodeEx](icordebugilframe4-getcodeex-method.md) 方法來判斷偵錯工具是否可以存取已檢測的 IL。</span><span class="sxs-lookup"><span data-stu-id="5aac8-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5aac8-113">需求</span><span class="sxs-lookup"><span data-stu-id="5aac8-113">Requirements</span></span>  
 <span data-ttu-id="5aac8-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5aac8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aac8-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5aac8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5aac8-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5aac8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5aac8-117">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5aac8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aac8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5aac8-118">See also</span></span>

- [<span data-ttu-id="5aac8-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="5aac8-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="5aac8-120">ICorDebugILFrame4 介面</span><span class="sxs-lookup"><span data-stu-id="5aac8-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="5aac8-121">ReJIT：操作指南</span><span class="sxs-lookup"><span data-stu-id="5aac8-121">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
