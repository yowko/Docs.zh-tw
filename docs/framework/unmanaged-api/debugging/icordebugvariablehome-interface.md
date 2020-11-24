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
ms.openlocfilehash: 089e68278113dfdf509ed848f424ad32baa145ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679542"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="9f5fc-102">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="9f5fc-102">ICorDebugVariableHome Interface</span></span>

<span data-ttu-id="9f5fc-103">表示函數的區域變數或引數。</span><span class="sxs-lookup"><span data-stu-id="9f5fc-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9f5fc-104">方法</span><span class="sxs-lookup"><span data-stu-id="9f5fc-104">Methods</span></span>  
  
|<span data-ttu-id="9f5fc-105">方法</span><span class="sxs-lookup"><span data-stu-id="9f5fc-105">Method</span></span>|<span data-ttu-id="9f5fc-106">描述</span><span class="sxs-lookup"><span data-stu-id="9f5fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f5fc-107">GetArgumentIndex 方法</span><span class="sxs-lookup"><span data-stu-id="9f5fc-107">GetArgumentIndex Method</span></span>](icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="9f5fc-108">取得函數引數的索引。</span><span class="sxs-lookup"><span data-stu-id="9f5fc-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="9f5fc-109">GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="9f5fc-109">GetCode Method</span></span>](icordebugvariablehome-getcode-method.md)|<span data-ttu-id="9f5fc-110">取得包含這個物件的 "ICorDebugCode" 實例 `ICorDebugVariableHome` 。</span><span class="sxs-lookup"><span data-stu-id="9f5fc-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="9f5fc-111">GetLiveRange 方法</span><span class="sxs-lookup"><span data-stu-id="9f5fc-111">GetLiveRange Method</span></span>](icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="9f5fc-112">取得這個變數的存留原生範圍。</span><span class="sxs-lookup"><span data-stu-id="9f5fc-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="9f5fc-113">GetLocationType 方法</span><span class="sxs-lookup"><span data-stu-id="9f5fc-113">GetLocationType Method</span></span>](icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="9f5fc-114">取得變數原生位置的型別。</span><span class="sxs-lookup"><span data-stu-id="9f5fc-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="9f5fc-115">GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="9f5fc-115">GetOffset Method</span></span>](icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="9f5fc-116">取得變數基底暫存器的位移。</span><span class="sxs-lookup"><span data-stu-id="9f5fc-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="9f5fc-117">GetRegister 方法</span><span class="sxs-lookup"><span data-stu-id="9f5fc-117">GetRegister Method</span></span>](icordebugvariablehome-getregister-method.md)|<span data-ttu-id="9f5fc-118">取得暫存器，其中包含位置類型為的變數 `VLT_REGISTER` ，以及位置類型為之變數的基底暫存器 `VLT_REGISTER_RELATIVE` 。</span><span class="sxs-lookup"><span data-stu-id="9f5fc-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="9f5fc-119">GetSlotIndex 方法</span><span class="sxs-lookup"><span data-stu-id="9f5fc-119">GetSlotIndex Method</span></span>](icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="9f5fc-120">取得本機變數的 managed 位置索引。</span><span class="sxs-lookup"><span data-stu-id="9f5fc-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9f5fc-121">範例</span><span class="sxs-lookup"><span data-stu-id="9f5fc-121">Example</span></span>  

 <span data-ttu-id="9f5fc-122">下列程式碼片段會使用名為的 [ICorDebugCode4](icordebugcode4-interface.md) 物件 `pCode4` 。</span><span class="sxs-lookup"><span data-stu-id="9f5fc-122">The following code fragment uses the [ICorDebugCode4](icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="9f5fc-123">需求</span><span class="sxs-lookup"><span data-stu-id="9f5fc-123">Requirements</span></span>  

 <span data-ttu-id="9f5fc-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9f5fc-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f5fc-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f5fc-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f5fc-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f5fc-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f5fc-127">**.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f5fc-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f5fc-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f5fc-128">See also</span></span>

- [<span data-ttu-id="9f5fc-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9f5fc-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9f5fc-130">ICorDebugVariableHomeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="9f5fc-130">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)
