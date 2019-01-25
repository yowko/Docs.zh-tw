---
title: ICorDebugVariableHome 介面
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78325236ab262c474e57b0d903033990b0e85f12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721917"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="27273-102">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="27273-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="27273-103">代表本機變數或函式的引數。</span><span class="sxs-lookup"><span data-stu-id="27273-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27273-104">方法</span><span class="sxs-lookup"><span data-stu-id="27273-104">Methods</span></span>  
  
|<span data-ttu-id="27273-105">方法</span><span class="sxs-lookup"><span data-stu-id="27273-105">Method</span></span>|<span data-ttu-id="27273-106">描述</span><span class="sxs-lookup"><span data-stu-id="27273-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27273-107">GetArgumentIndex 方法</span><span class="sxs-lookup"><span data-stu-id="27273-107">GetArgumentIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="27273-108">取得函式引數的索引。</span><span class="sxs-lookup"><span data-stu-id="27273-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="27273-109">GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="27273-109">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|<span data-ttu-id="27273-110">取得包含此 「 ICorDebugCode 」 執行個體`ICorDebugVariableHome`物件。</span><span class="sxs-lookup"><span data-stu-id="27273-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="27273-111">GetLiveRange 方法</span><span class="sxs-lookup"><span data-stu-id="27273-111">GetLiveRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="27273-112">取得原生的此變數是即時的範圍。</span><span class="sxs-lookup"><span data-stu-id="27273-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="27273-113">GetLocationType 方法</span><span class="sxs-lookup"><span data-stu-id="27273-113">GetLocationType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="27273-114">取得變數的原生位置類型。</span><span class="sxs-lookup"><span data-stu-id="27273-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="27273-115">GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="27273-115">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="27273-116">取得從基底的暫存器變數的位移。</span><span class="sxs-lookup"><span data-stu-id="27273-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="27273-117">GetRegister 方法</span><span class="sxs-lookup"><span data-stu-id="27273-117">GetRegister Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|<span data-ttu-id="27273-118">取得包含位置類型的變數的暫存`VLT_REGISTER`，及基底的位置類型的變數報名`VLT_REGISTER_RELATIVE`。</span><span class="sxs-lookup"><span data-stu-id="27273-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="27273-119">GetSlotIndex 方法</span><span class="sxs-lookup"><span data-stu-id="27273-119">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="27273-120">取得區域變數的 managed 的位置索引。</span><span class="sxs-lookup"><span data-stu-id="27273-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="27273-121">範例</span><span class="sxs-lookup"><span data-stu-id="27273-121">Example</span></span>  
 <span data-ttu-id="27273-122">下列程式碼片段會使用[ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)名為物件`pCode4`。</span><span class="sxs-lookup"><span data-stu-id="27273-122">The following code fragment uses the [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="27273-123">需求</span><span class="sxs-lookup"><span data-stu-id="27273-123">Requirements</span></span>  
 <span data-ttu-id="27273-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27273-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27273-125">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27273-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27273-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27273-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27273-127">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27273-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27273-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27273-128">See also</span></span>
- [<span data-ttu-id="27273-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="27273-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="27273-130">ICorDebugVariableHomeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="27273-130">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
