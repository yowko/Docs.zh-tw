---
title: ICorDebugVariableSymbol::GetSlotIndex Method
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: fc42517cb95dfc14c472b5bb9111ebd70639cee7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725985"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="f4440-102">ICorDebugVariableSymbol::GetSlotIndex Method</span><span class="sxs-lookup"><span data-stu-id="f4440-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>

<span data-ttu-id="f4440-103">取得區域變數的 Managed 位置索引。</span><span class="sxs-lookup"><span data-stu-id="f4440-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4440-104">語法</span><span class="sxs-lookup"><span data-stu-id="f4440-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4440-105">參數</span><span class="sxs-lookup"><span data-stu-id="f4440-105">Parameters</span></span>  

 `pSlotIndex`  
 <span data-ttu-id="f4440-106">[out] 區域變數位置索引的指標。</span><span class="sxs-lookup"><span data-stu-id="f4440-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4440-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f4440-107">Return Value</span></span>  

 <span data-ttu-id="f4440-108">如果成功，則為 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="f4440-108">`S_OK` if successful.</span></span> <span data-ttu-id="f4440-109">如果變數是函式引數，則為 `E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="f4440-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4440-110">備註</span><span class="sxs-lookup"><span data-stu-id="f4440-110">Remarks</span></span>  

 <span data-ttu-id="f4440-111">區域變數的 Managed 位置索引可用來擷取變數的中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="f4440-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4440-112">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="f4440-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4440-113">需求</span><span class="sxs-lookup"><span data-stu-id="f4440-113">Requirements</span></span>  

 <span data-ttu-id="f4440-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f4440-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4440-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4440-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4440-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4440-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4440-117">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4440-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4440-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4440-118">See also</span></span>

- [<span data-ttu-id="f4440-119">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="f4440-119">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="f4440-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f4440-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
