---
title: ICorDebugVariableSymbol::GetSlotIndex Method
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: abb84e529768e0be44883511bb89703a4c3199df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="21b83-102">ICorDebugVariableSymbol::GetSlotIndex Method</span><span class="sxs-lookup"><span data-stu-id="21b83-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="21b83-103">取得區域變數的 Managed 位置索引。</span><span class="sxs-lookup"><span data-stu-id="21b83-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21b83-104">語法</span><span class="sxs-lookup"><span data-stu-id="21b83-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21b83-105">參數</span><span class="sxs-lookup"><span data-stu-id="21b83-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="21b83-106">[out] 區域變數位置索引的指標。</span><span class="sxs-lookup"><span data-stu-id="21b83-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21b83-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="21b83-107">Return Value</span></span>  
 <span data-ttu-id="21b83-108">如果成功，則為 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="21b83-108">`S_OK` if successful.</span></span> <span data-ttu-id="21b83-109">如果變數是函式引數，則為 `E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="21b83-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21b83-110">備註</span><span class="sxs-lookup"><span data-stu-id="21b83-110">Remarks</span></span>  
 <span data-ttu-id="21b83-111">區域變數的 Managed 位置索引可用來擷取變數的中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="21b83-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21b83-112">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="21b83-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21b83-113">需求</span><span class="sxs-lookup"><span data-stu-id="21b83-113">Requirements</span></span>  
 <span data-ttu-id="21b83-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21b83-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21b83-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21b83-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21b83-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21b83-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21b83-117">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21b83-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b83-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="21b83-118">See Also</span></span>  
 [<span data-ttu-id="21b83-119">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="21b83-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="21b83-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="21b83-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
