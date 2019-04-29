---
title: CorDebugCodeInvokePurpose 列舉
ms.date: 03/30/2017
api_name:
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 858dfe9b15422680a261fef9e22d8c89d9d7fe45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609125"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="ad852-102">CorDebugCodeInvokePurpose 列舉</span><span class="sxs-lookup"><span data-stu-id="ad852-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="ad852-103">描述匯出函式呼叫 Managed 程式碼的原因。</span><span class="sxs-lookup"><span data-stu-id="ad852-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad852-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad852-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="ad852-105">成員</span><span class="sxs-lookup"><span data-stu-id="ad852-105">Members</span></span>  
  
|<span data-ttu-id="ad852-106">成員</span><span class="sxs-lookup"><span data-stu-id="ad852-106">Member</span></span>|<span data-ttu-id="ad852-107">描述</span><span class="sxs-lookup"><span data-stu-id="ad852-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="ad852-108">無或未知。</span><span class="sxs-lookup"><span data-stu-id="ad852-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="ad852-109">Managed 程式碼會執行任何 Managed 進入點，例如反向 p-invoke。</span><span class="sxs-lookup"><span data-stu-id="ad852-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="ad852-110">執行階段不知道其他任何詳細目的。</span><span class="sxs-lookup"><span data-stu-id="ad852-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="ad852-111">Managed 程式碼會執行靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="ad852-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="ad852-112">Managed 程式碼會執行所呼叫之一些介面方法的實作。</span><span class="sxs-lookup"><span data-stu-id="ad852-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad852-113">備註</span><span class="sxs-lookup"><span data-stu-id="ad852-113">Remarks</span></span>  
 <span data-ttu-id="ad852-114">這個列舉型別由[ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)方法，以提供資訊逐步執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ad852-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad852-115">這個列舉僅適用於 .NET Native 偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="ad852-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad852-116">需求</span><span class="sxs-lookup"><span data-stu-id="ad852-116">Requirements</span></span>  
 <span data-ttu-id="ad852-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad852-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad852-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad852-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad852-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad852-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad852-120">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad852-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad852-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad852-121">See also</span></span>

- [<span data-ttu-id="ad852-122">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="ad852-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="ad852-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="ad852-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
