---
title: ICorDebugClass2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: 795e9f4862992d95eeef98a986545cca47d828c6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784146"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="439a1-102">ICorDebugClass2 介面</span><span class="sxs-lookup"><span data-stu-id="439a1-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="439a1-103">表示泛型類別，或是具有 <xref:System.Type> 類型之方法參數的類別。</span><span class="sxs-lookup"><span data-stu-id="439a1-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="439a1-104">這個介面會擴充[ICorDebugClass](icordebugclass-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="439a1-104">This interface extends [ICorDebugClass](icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="439a1-105">方法</span><span class="sxs-lookup"><span data-stu-id="439a1-105">Methods</span></span>  
  
|<span data-ttu-id="439a1-106">方法</span><span class="sxs-lookup"><span data-stu-id="439a1-106">Method</span></span>|<span data-ttu-id="439a1-107">描述</span><span class="sxs-lookup"><span data-stu-id="439a1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="439a1-108">GetParameterizedType 方法</span><span class="sxs-lookup"><span data-stu-id="439a1-108">GetParameterizedType Method</span></span>](icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="439a1-109">取得這個類別的類型宣告。</span><span class="sxs-lookup"><span data-stu-id="439a1-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="439a1-110">SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="439a1-110">SetJMCStatus Method</span></span>](icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="439a1-111">針對這個類別的每個方法，設定一個值，指出此方法是否為使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="439a1-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="439a1-112">備註</span><span class="sxs-lookup"><span data-stu-id="439a1-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="439a1-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="439a1-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="439a1-114">需求</span><span class="sxs-lookup"><span data-stu-id="439a1-114">Requirements</span></span>  
 <span data-ttu-id="439a1-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="439a1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="439a1-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="439a1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="439a1-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="439a1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="439a1-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="439a1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="439a1-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="439a1-119">See also</span></span>

- [<span data-ttu-id="439a1-120">ICorDebugClass 介面</span><span class="sxs-lookup"><span data-stu-id="439a1-120">ICorDebugClass Interface</span></span>](icordebugclass-interface.md)
- [<span data-ttu-id="439a1-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="439a1-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
