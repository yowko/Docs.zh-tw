---
title: ICorDebugVariableSymbol::GetSlotIndex Method
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: affe67006c9e37d55b0f9d107c92441da44c9ab8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768819"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="3c0b5-102">ICorDebugVariableSymbol::GetSlotIndex Method</span><span class="sxs-lookup"><span data-stu-id="3c0b5-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="3c0b5-103">取得區域變數的 Managed 位置索引。</span><span class="sxs-lookup"><span data-stu-id="3c0b5-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c0b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c0b5-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c0b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="3c0b5-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="3c0b5-106">[out] 區域變數位置索引的指標。</span><span class="sxs-lookup"><span data-stu-id="3c0b5-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c0b5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="3c0b5-107">Return Value</span></span>  
 <span data-ttu-id="3c0b5-108">如果成功，則為 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="3c0b5-108">`S_OK` if successful.</span></span> <span data-ttu-id="3c0b5-109">如果變數是函式引數，則為 `E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="3c0b5-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c0b5-110">備註</span><span class="sxs-lookup"><span data-stu-id="3c0b5-110">Remarks</span></span>  
 <span data-ttu-id="3c0b5-111">區域變數的 Managed 位置索引可用來擷取變數的中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="3c0b5-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c0b5-112">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="3c0b5-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c0b5-113">需求</span><span class="sxs-lookup"><span data-stu-id="3c0b5-113">Requirements</span></span>  
 <span data-ttu-id="3c0b5-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c0b5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c0b5-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c0b5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c0b5-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c0b5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c0b5-117">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c0b5-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c0b5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c0b5-118">See also</span></span>

- [<span data-ttu-id="3c0b5-119">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="3c0b5-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="3c0b5-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3c0b5-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
