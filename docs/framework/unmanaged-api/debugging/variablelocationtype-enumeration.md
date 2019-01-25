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
ms.openlocfilehash: dd1a622faa095836a3d5c22c7a18084482074c2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653212"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="b5ec9-102">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="b5ec9-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="b5ec9-103">表示變數的原生位置型別。</span><span class="sxs-lookup"><span data-stu-id="b5ec9-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5ec9-104">語法</span><span class="sxs-lookup"><span data-stu-id="b5ec9-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="b5ec9-105">成員</span><span class="sxs-lookup"><span data-stu-id="b5ec9-105">Members</span></span>  
  
|<span data-ttu-id="b5ec9-106">成員</span><span class="sxs-lookup"><span data-stu-id="b5ec9-106">Member</span></span>|<span data-ttu-id="b5ec9-107">描述</span><span class="sxs-lookup"><span data-stu-id="b5ec9-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="b5ec9-108">變數是在暫存器。</span><span class="sxs-lookup"><span data-stu-id="b5ec9-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="b5ec9-109">變數是在暫存器的相對記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="b5ec9-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="b5ec9-110">變數不會儲存在暫存器或暫存器的相對記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="b5ec9-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5ec9-111">備註</span><span class="sxs-lookup"><span data-stu-id="b5ec9-111">Remarks</span></span>  
 <span data-ttu-id="b5ec9-112">成員`VariableLocationType`列舉型別由[ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b5ec9-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5ec9-113">需求</span><span class="sxs-lookup"><span data-stu-id="b5ec9-113">Requirements</span></span>  
 <span data-ttu-id="b5ec9-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b5ec9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5ec9-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5ec9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5ec9-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5ec9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5ec9-117">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5ec9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ec9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5ec9-118">See also</span></span>
- [<span data-ttu-id="b5ec9-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="b5ec9-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
