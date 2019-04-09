---
title: VariableLocationType 列舉
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 392254efcd099aca60e58b3cc0bc61ca85aa2c66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099946"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="25a6f-102">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="25a6f-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="25a6f-103">表示變數的原生位置型別。</span><span class="sxs-lookup"><span data-stu-id="25a6f-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25a6f-104">語法</span><span class="sxs-lookup"><span data-stu-id="25a6f-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="25a6f-105">成員</span><span class="sxs-lookup"><span data-stu-id="25a6f-105">Members</span></span>  
  
|<span data-ttu-id="25a6f-106">成員</span><span class="sxs-lookup"><span data-stu-id="25a6f-106">Member</span></span>|<span data-ttu-id="25a6f-107">描述</span><span class="sxs-lookup"><span data-stu-id="25a6f-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="25a6f-108">變數是在暫存器。</span><span class="sxs-lookup"><span data-stu-id="25a6f-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="25a6f-109">變數是在暫存器的相對記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="25a6f-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="25a6f-110">變數不會儲存在暫存器或暫存器的相對記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="25a6f-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25a6f-111">備註</span><span class="sxs-lookup"><span data-stu-id="25a6f-111">Remarks</span></span>  
 <span data-ttu-id="25a6f-112">成員`VariableLocationType`列舉型別由[ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="25a6f-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25a6f-113">需求</span><span class="sxs-lookup"><span data-stu-id="25a6f-113">Requirements</span></span>  
 <span data-ttu-id="25a6f-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25a6f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25a6f-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25a6f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25a6f-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25a6f-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="25a6f-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="25a6f-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="25a6f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25a6f-118">See also</span></span>

- [<span data-ttu-id="25a6f-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="25a6f-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
