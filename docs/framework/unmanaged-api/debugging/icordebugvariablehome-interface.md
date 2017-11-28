---
title: "ICorDebugVariableHome 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ICorDebugVariableHome
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome
helpviewer_keywords: ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ea8f4033a6b0878288c49d6f6d964eb40675162d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="148c9-102">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="148c9-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="148c9-103">代表本機變數或函式的引數。</span><span class="sxs-lookup"><span data-stu-id="148c9-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="148c9-104">方法</span><span class="sxs-lookup"><span data-stu-id="148c9-104">Methods</span></span>  
  
|<span data-ttu-id="148c9-105">方法</span><span class="sxs-lookup"><span data-stu-id="148c9-105">Method</span></span>|<span data-ttu-id="148c9-106">說明</span><span class="sxs-lookup"><span data-stu-id="148c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="148c9-107">GetArgumentIndex 方法</span><span class="sxs-lookup"><span data-stu-id="148c9-107">GetArgumentIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="148c9-108">取得函式引數索引。</span><span class="sxs-lookup"><span data-stu-id="148c9-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="148c9-109">GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="148c9-109">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|<span data-ttu-id="148c9-110">取得"ICorDebugCode 」 執行個體包含這個`ICorDebugVariableHome`物件。</span><span class="sxs-lookup"><span data-stu-id="148c9-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="148c9-111">GetLiveRange 方法</span><span class="sxs-lookup"><span data-stu-id="148c9-111">GetLiveRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="148c9-112">取得原生的此變數是即時的範圍。</span><span class="sxs-lookup"><span data-stu-id="148c9-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="148c9-113">GetLocationType 方法</span><span class="sxs-lookup"><span data-stu-id="148c9-113">GetLocationType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="148c9-114">取得變數的原生位置類型。</span><span class="sxs-lookup"><span data-stu-id="148c9-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="148c9-115">GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="148c9-115">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="148c9-116">取得從基底暫存器變數位移。</span><span class="sxs-lookup"><span data-stu-id="148c9-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="148c9-117">GetRegister 方法</span><span class="sxs-lookup"><span data-stu-id="148c9-117">GetRegister Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|<span data-ttu-id="148c9-118">取得包含變數的位置類型的暫存器`VLT_REGISTER`，和基底暫存器變數的位置類型`VLT_REGISTER_RELATIVE`。</span><span class="sxs-lookup"><span data-stu-id="148c9-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="148c9-119">GetSlotIndex 方法</span><span class="sxs-lookup"><span data-stu-id="148c9-119">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="148c9-120">取得區域變數的 managed 的位置索引。</span><span class="sxs-lookup"><span data-stu-id="148c9-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="148c9-121">範例</span><span class="sxs-lookup"><span data-stu-id="148c9-121">Example</span></span>  
 <span data-ttu-id="148c9-122">下列程式碼片段使用[ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)名為物件`pCode4`。</span><span class="sxs-lookup"><span data-stu-id="148c9-122">The following code fragment uses the [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="148c9-123">需求</span><span class="sxs-lookup"><span data-stu-id="148c9-123">Requirements</span></span>  
 <span data-ttu-id="148c9-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="148c9-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="148c9-125">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="148c9-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="148c9-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="148c9-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="148c9-127">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="148c9-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="148c9-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="148c9-128">See Also</span></span>  
 [<span data-ttu-id="148c9-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="148c9-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="148c9-130">ICorDebugVariableHomeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="148c9-130">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
