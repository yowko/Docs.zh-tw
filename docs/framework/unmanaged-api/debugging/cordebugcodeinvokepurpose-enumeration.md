---
title: "CorDebugCodeInvokePurpose 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugInvokePurpose
api_location: mscordbi.dll
api_type: COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e87e5d8baf3ff7c87efe8f6bd96f8fd806527363
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="c2d38-102">CorDebugCodeInvokePurpose 列舉</span><span class="sxs-lookup"><span data-stu-id="c2d38-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="c2d38-103">描述匯出函式呼叫 Managed 程式碼的原因。</span><span class="sxs-lookup"><span data-stu-id="c2d38-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2d38-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2d38-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="c2d38-105">成員</span><span class="sxs-lookup"><span data-stu-id="c2d38-105">Members</span></span>  
  
|<span data-ttu-id="c2d38-106">成員</span><span class="sxs-lookup"><span data-stu-id="c2d38-106">Member</span></span>|<span data-ttu-id="c2d38-107">描述</span><span class="sxs-lookup"><span data-stu-id="c2d38-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="c2d38-108">無或未知。</span><span class="sxs-lookup"><span data-stu-id="c2d38-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="c2d38-109">Managed 程式碼會執行任何 Managed 進入點，例如反向 p-invoke。</span><span class="sxs-lookup"><span data-stu-id="c2d38-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="c2d38-110">執行階段不知道其他任何詳細目的。</span><span class="sxs-lookup"><span data-stu-id="c2d38-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="c2d38-111">Managed 程式碼會執行靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="c2d38-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="c2d38-112">Managed 程式碼會執行所呼叫之一些介面方法的實作。</span><span class="sxs-lookup"><span data-stu-id="c2d38-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2d38-113">備註</span><span class="sxs-lookup"><span data-stu-id="c2d38-113">Remarks</span></span>  
 <span data-ttu-id="c2d38-114">這個列舉型別由[icordebugprocess6:: Getexportstepinfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)方法以提供資訊逐步執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="c2d38-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2d38-115">這個列舉僅適用於 .NET 原生偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="c2d38-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2d38-116">需求</span><span class="sxs-lookup"><span data-stu-id="c2d38-116">Requirements</span></span>  
 <span data-ttu-id="c2d38-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2d38-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2d38-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2d38-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2d38-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2d38-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2d38-120">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2d38-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d38-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="c2d38-121">See Also</span></span>  
 [<span data-ttu-id="c2d38-122">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="c2d38-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="c2d38-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="c2d38-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
