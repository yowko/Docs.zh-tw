---
title: ICorDebugType2：： GetTypeID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
ms.openlocfilehash: 944313893d88b8eff97291d2517e4863a5ae958a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092768"
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="bdb7a-102">ICorDebugType2：： GetTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="bdb7a-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="bdb7a-103">取得此類型的[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) 。</span><span class="sxs-lookup"><span data-stu-id="bdb7a-103">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdb7a-104">語法</span><span class="sxs-lookup"><span data-stu-id="bdb7a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdb7a-105">參數</span><span class="sxs-lookup"><span data-stu-id="bdb7a-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="bdb7a-106">脫銷此 ICorDebugType 之[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)的指標。</span><span class="sxs-lookup"><span data-stu-id="bdb7a-106">[out] A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bdb7a-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="bdb7a-107">Return Value</span></span>  
 <span data-ttu-id="bdb7a-108">如果成功，傳回值為 `S_OK`，如果失敗，則傳回失敗 `HRESULT` 程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdb7a-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="bdb7a-109">`HRESULT` 碼包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="bdb7a-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="bdb7a-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="bdb7a-110">Return code</span></span>|<span data-ttu-id="bdb7a-111">描述</span><span class="sxs-lookup"><span data-stu-id="bdb7a-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="bdb7a-112">方法成功。</span><span class="sxs-lookup"><span data-stu-id="bdb7a-112">Method succeeded.</span></span> <span data-ttu-id="bdb7a-113">方法已取出有效的[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="bdb7a-113">The method has retrieved a valid [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="bdb7a-114">尚未載入類型。</span><span class="sxs-lookup"><span data-stu-id="bdb7a-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="bdb7a-115">不支援此類型。</span><span class="sxs-lookup"><span data-stu-id="bdb7a-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdb7a-116">備註</span><span class="sxs-lookup"><span data-stu-id="bdb7a-116">Remarks</span></span>  
 <span data-ttu-id="bdb7a-117">這個方法會提供 ICorDebugType 的對應，其代表可能或可能尚未載入執行時間中的類型到[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)，這是用來識別載入執行時間之類型的不透明控制碼。</span><span class="sxs-lookup"><span data-stu-id="bdb7a-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="bdb7a-118">當 ICorDebugType 所代表的類型尚未載入時，這個方法會傳回 `CORDBG_E_CLASS_NOT_LOADED`。</span><span class="sxs-lookup"><span data-stu-id="bdb7a-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="bdb7a-119">如果不支援此類型，它會傳回 `CORDBG_E_UNSUPPORTED`。</span><span class="sxs-lookup"><span data-stu-id="bdb7a-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdb7a-120">需求</span><span class="sxs-lookup"><span data-stu-id="bdb7a-120">Requirements</span></span>  
 <span data-ttu-id="bdb7a-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bdb7a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdb7a-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdb7a-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdb7a-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdb7a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdb7a-124">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdb7a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb7a-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="bdb7a-125">See also</span></span>

- [<span data-ttu-id="bdb7a-126">ICorDebugType2 介面</span><span class="sxs-lookup"><span data-stu-id="bdb7a-126">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
