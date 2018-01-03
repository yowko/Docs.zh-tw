---
title: ICorDebugClass2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass2
helpviewer_keywords: ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5053ea14ac7a8af33319bbbb289db01dbbc86169
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclass2-interface1"></a><span data-ttu-id="47488-102">ICorDebugClass2 Interface1</span><span class="sxs-lookup"><span data-stu-id="47488-102">ICorDebugClass2 Interface1</span></span>
<span data-ttu-id="47488-103">表示泛型類別，或是具有 <xref:System.Type> 類型之方法參數的類別。</span><span class="sxs-lookup"><span data-stu-id="47488-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="47488-104">這個介面延伸[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="47488-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="47488-105">方法</span><span class="sxs-lookup"><span data-stu-id="47488-105">Methods</span></span>  
  
|<span data-ttu-id="47488-106">方法</span><span class="sxs-lookup"><span data-stu-id="47488-106">Method</span></span>|<span data-ttu-id="47488-107">描述</span><span class="sxs-lookup"><span data-stu-id="47488-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="47488-108">GetParameterizedType 方法</span><span class="sxs-lookup"><span data-stu-id="47488-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="47488-109">取得這個類別的型別宣告。</span><span class="sxs-lookup"><span data-stu-id="47488-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="47488-110">SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="47488-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="47488-111">這個類別的每個方法，設定值，指出方法是否為使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="47488-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47488-112">備註</span><span class="sxs-lookup"><span data-stu-id="47488-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47488-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="47488-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47488-114">需求</span><span class="sxs-lookup"><span data-stu-id="47488-114">Requirements</span></span>  
 <span data-ttu-id="47488-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47488-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47488-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47488-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47488-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47488-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47488-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47488-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47488-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="47488-119">See Also</span></span>  
 [<span data-ttu-id="47488-120">ICorDebugClass 介面 1</span><span class="sxs-lookup"><span data-stu-id="47488-120">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 [<span data-ttu-id="47488-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="47488-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
