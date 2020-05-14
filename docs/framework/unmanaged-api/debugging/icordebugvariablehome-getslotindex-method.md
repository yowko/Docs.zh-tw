---
title: ICorDebugVariableHome：： GetSlotIndex 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 0bffd2db0a4a061a8629ff50a03a319feec6d836
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396557"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="d54c8-102">ICorDebugVariableHome：： GetSlotIndex 方法</span><span class="sxs-lookup"><span data-stu-id="d54c8-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="d54c8-103">取得本機變數的 managed 位置索引。</span><span class="sxs-lookup"><span data-stu-id="d54c8-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d54c8-104">語法</span><span class="sxs-lookup"><span data-stu-id="d54c8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d54c8-105">參數</span><span class="sxs-lookup"><span data-stu-id="d54c8-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="d54c8-106">脫銷本機變數位置索引的指標。</span><span class="sxs-lookup"><span data-stu-id="d54c8-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d54c8-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d54c8-107">Return Value</span></span>  
 <span data-ttu-id="d54c8-108">方法會傳回下列值。</span><span class="sxs-lookup"><span data-stu-id="d54c8-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="d54c8-109">值</span><span class="sxs-lookup"><span data-stu-id="d54c8-109">Value</span></span>|<span data-ttu-id="d54c8-110">說明</span><span class="sxs-lookup"><span data-stu-id="d54c8-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="d54c8-111">方法呼叫會傳回中的位置索引值 `pSlotIndex` 。</span><span class="sxs-lookup"><span data-stu-id="d54c8-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="d54c8-112">目前的[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例代表函式引數。</span><span class="sxs-lookup"><span data-stu-id="d54c8-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d54c8-113">備註</span><span class="sxs-lookup"><span data-stu-id="d54c8-113">Remarks</span></span>  
 <span data-ttu-id="d54c8-114">位置索引可以用來抓取此區域變數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d54c8-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d54c8-115">需求</span><span class="sxs-lookup"><span data-stu-id="d54c8-115">Requirements</span></span>  
 <span data-ttu-id="d54c8-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d54c8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d54c8-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d54c8-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d54c8-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d54c8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d54c8-119">**.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d54c8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d54c8-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="d54c8-120">See also</span></span>

- [<span data-ttu-id="d54c8-121">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="d54c8-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
