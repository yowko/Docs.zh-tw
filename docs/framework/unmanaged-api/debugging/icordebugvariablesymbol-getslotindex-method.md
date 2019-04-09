---
title: ICorDebugVariableSymbol::GetSlotIndex Method
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: affe67006c9e37d55b0f9d107c92441da44c9ab8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138784"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="2c6c1-102">ICorDebugVariableSymbol::GetSlotIndex Method</span><span class="sxs-lookup"><span data-stu-id="2c6c1-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="2c6c1-103">取得區域變數的 Managed 位置索引。</span><span class="sxs-lookup"><span data-stu-id="2c6c1-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c6c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c6c1-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c6c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="2c6c1-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="2c6c1-106">[out] 區域變數位置索引的指標。</span><span class="sxs-lookup"><span data-stu-id="2c6c1-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c6c1-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="2c6c1-107">Return Value</span></span>  
 `S_OK` <span data-ttu-id="2c6c1-108">如果成功。</span><span class="sxs-lookup"><span data-stu-id="2c6c1-108">if successful.</span></span> `E_FAIL` <span data-ttu-id="2c6c1-109">如果變數是函式引數。</span><span class="sxs-lookup"><span data-stu-id="2c6c1-109">if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c6c1-110">備註</span><span class="sxs-lookup"><span data-stu-id="2c6c1-110">Remarks</span></span>  
 <span data-ttu-id="2c6c1-111">區域變數的 Managed 位置索引可用來擷取變數的中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="2c6c1-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c6c1-112">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="2c6c1-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c6c1-113">需求</span><span class="sxs-lookup"><span data-stu-id="2c6c1-113">Requirements</span></span>  
 <span data-ttu-id="2c6c1-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c6c1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c6c1-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c6c1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c6c1-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c6c1-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2c6c1-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="2c6c1-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2c6c1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c6c1-118">See also</span></span>

- [<span data-ttu-id="2c6c1-119">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="2c6c1-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="2c6c1-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2c6c1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
