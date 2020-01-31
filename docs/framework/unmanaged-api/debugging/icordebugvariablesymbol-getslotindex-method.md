---
title: ICorDebugVariableSymbol::GetSlotIndex Method
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: 3510daffb55bdb22aa5f835bf27157e7c8428509
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790898"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="56288-102">ICorDebugVariableSymbol::GetSlotIndex Method</span><span class="sxs-lookup"><span data-stu-id="56288-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="56288-103">取得區域變數的 Managed 位置索引。</span><span class="sxs-lookup"><span data-stu-id="56288-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56288-104">語法</span><span class="sxs-lookup"><span data-stu-id="56288-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56288-105">參數</span><span class="sxs-lookup"><span data-stu-id="56288-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="56288-106">[out] 區域變數位置索引的指標。</span><span class="sxs-lookup"><span data-stu-id="56288-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56288-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="56288-107">Return Value</span></span>  
 <span data-ttu-id="56288-108">如果成功，則為 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="56288-108">`S_OK` if successful.</span></span> <span data-ttu-id="56288-109">如果變數是函式引數，則為 `E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="56288-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56288-110">備註</span><span class="sxs-lookup"><span data-stu-id="56288-110">Remarks</span></span>  
 <span data-ttu-id="56288-111">區域變數的 Managed 位置索引可用來擷取變數的中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="56288-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56288-112">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="56288-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56288-113">需求</span><span class="sxs-lookup"><span data-stu-id="56288-113">Requirements</span></span>  
 <span data-ttu-id="56288-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="56288-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56288-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56288-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56288-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56288-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56288-117">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56288-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56288-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="56288-118">See also</span></span>

- [<span data-ttu-id="56288-119">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="56288-119">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="56288-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="56288-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
