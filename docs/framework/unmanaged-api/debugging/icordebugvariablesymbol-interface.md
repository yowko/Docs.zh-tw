---
title: ICorDebugVariableSymbol 介面
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 3d808fd49eb7767f1f48ad4e07d8ba7e47c8f34b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679477"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="3f845-102">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="3f845-102">ICorDebugVariableSymbol Interface</span></span>

<span data-ttu-id="3f845-103">擷取變數的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="3f845-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f845-104">方法</span><span class="sxs-lookup"><span data-stu-id="3f845-104">Methods</span></span>  
  
|<span data-ttu-id="3f845-105">方法</span><span class="sxs-lookup"><span data-stu-id="3f845-105">Method</span></span>|<span data-ttu-id="3f845-106">描述</span><span class="sxs-lookup"><span data-stu-id="3f845-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f845-107">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="3f845-107">GetName Method</span></span>](icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="3f845-108">取得變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3f845-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="3f845-109">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="3f845-109">GetSize Method</span></span>](icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="3f845-110">取得變數的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="3f845-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="3f845-111">GetSlotIndex 方法</span><span class="sxs-lookup"><span data-stu-id="3f845-111">GetSlotIndex Method</span></span>](icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="3f845-112">取得區域變數的 Managed 位置索引。</span><span class="sxs-lookup"><span data-stu-id="3f845-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="3f845-113">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="3f845-113">GetValue Method</span></span>](icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="3f845-114">取得變數的值做為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="3f845-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="3f845-115">SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="3f845-115">SetValue Method</span></span>](icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="3f845-116">指派位元組陣列的值給變數。</span><span class="sxs-lookup"><span data-stu-id="3f845-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f845-117">備註</span><span class="sxs-lookup"><span data-stu-id="3f845-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f845-118">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="3f845-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="3f845-119">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="3f845-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f845-120">需求</span><span class="sxs-lookup"><span data-stu-id="3f845-120">Requirements</span></span>  

 <span data-ttu-id="3f845-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f845-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f845-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f845-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f845-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f845-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f845-124">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f845-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f845-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f845-125">See also</span></span>

- [<span data-ttu-id="3f845-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3f845-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3f845-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="3f845-127">Debugging</span></span>](index.md)
