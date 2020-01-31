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
ms.openlocfilehash: 542bfa05c55ef224d1b9111f9af6c069e9e23542
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790976"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="5dee9-102">ICorDebugVariableHome：： GetSlotIndex 方法</span><span class="sxs-lookup"><span data-stu-id="5dee9-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="5dee9-103">取得本機變數的 managed 位置索引。</span><span class="sxs-lookup"><span data-stu-id="5dee9-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dee9-104">語法</span><span class="sxs-lookup"><span data-stu-id="5dee9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dee9-105">參數</span><span class="sxs-lookup"><span data-stu-id="5dee9-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="5dee9-106">脫銷本機變數位置索引的指標。</span><span class="sxs-lookup"><span data-stu-id="5dee9-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5dee9-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5dee9-107">Return Value</span></span>  
 <span data-ttu-id="5dee9-108">方法會傳回下列值。</span><span class="sxs-lookup"><span data-stu-id="5dee9-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="5dee9-109">{2&gt;值&lt;2}</span><span class="sxs-lookup"><span data-stu-id="5dee9-109">Value</span></span>|<span data-ttu-id="5dee9-110">描述</span><span class="sxs-lookup"><span data-stu-id="5dee9-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="5dee9-111">方法呼叫會在 `pSlotIndex`中傳回位置索引值。</span><span class="sxs-lookup"><span data-stu-id="5dee9-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="5dee9-112">目前的[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例代表函式引數。</span><span class="sxs-lookup"><span data-stu-id="5dee9-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dee9-113">備註</span><span class="sxs-lookup"><span data-stu-id="5dee9-113">Remarks</span></span>  
 <span data-ttu-id="5dee9-114">位置索引可以用來抓取此區域變數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5dee9-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dee9-115">需求</span><span class="sxs-lookup"><span data-stu-id="5dee9-115">Requirements</span></span>  
 <span data-ttu-id="5dee9-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5dee9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dee9-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5dee9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5dee9-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dee9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dee9-119">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dee9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dee9-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="5dee9-120">See also</span></span>

- [<span data-ttu-id="5dee9-121">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="5dee9-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
