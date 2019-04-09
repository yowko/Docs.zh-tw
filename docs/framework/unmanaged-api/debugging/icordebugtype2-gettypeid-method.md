---
title: ICorDebugType2::GetTypeID 方法
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b19efdedc21f66e4692ce1850eb3947f856e436
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083747"
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="0a685-102">ICorDebugType2::GetTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="0a685-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="0a685-103">取得[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)這種類型。</span><span class="sxs-lookup"><span data-stu-id="0a685-103">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a685-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a685-104">Syntax</span></span>  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a685-105">參數</span><span class="sxs-lookup"><span data-stu-id="0a685-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="0a685-106">[out]指標[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)此 icordebugtype。</span><span class="sxs-lookup"><span data-stu-id="0a685-106">[out] A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a685-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="0a685-107">Return Value</span></span>  
 <span data-ttu-id="0a685-108">如果成功，傳回值為 `S_OK`，如果失敗，則傳回失敗 `HRESULT` 程式碼。</span><span class="sxs-lookup"><span data-stu-id="0a685-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="0a685-109">`HRESULT`碼包括下列：</span><span class="sxs-lookup"><span data-stu-id="0a685-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="0a685-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="0a685-110">Return code</span></span>|<span data-ttu-id="0a685-111">描述</span><span class="sxs-lookup"><span data-stu-id="0a685-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="0a685-112">方法成功。</span><span class="sxs-lookup"><span data-stu-id="0a685-112">Method succeeded.</span></span> <span data-ttu-id="0a685-113">此方法已擷取的有效[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="0a685-113">The method has retrieved a valid [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="0a685-114">尚未載入的型別。</span><span class="sxs-lookup"><span data-stu-id="0a685-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="0a685-115">不支援的類型。</span><span class="sxs-lookup"><span data-stu-id="0a685-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a685-116">備註</span><span class="sxs-lookup"><span data-stu-id="0a685-116">Remarks</span></span>  
 <span data-ttu-id="0a685-117">這個方法提供 ICorDebugType，表示可能會或可能已載入至執行階段，為的類型對應[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)，這可充當不透明處理識別載入執行階段型別。</span><span class="sxs-lookup"><span data-stu-id="0a685-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="0a685-118">當 ICorDebugType 表示的型別尚未被載入，則這個方法會傳回`CORDBG_E_CLASS_NOT_LOADED`。</span><span class="sxs-lookup"><span data-stu-id="0a685-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="0a685-119">如果不支援的類型，它會傳回`CORDBG_E_UNSUPPORTED`。</span><span class="sxs-lookup"><span data-stu-id="0a685-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a685-120">需求</span><span class="sxs-lookup"><span data-stu-id="0a685-120">Requirements</span></span>  
 <span data-ttu-id="0a685-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a685-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a685-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a685-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a685-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a685-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0a685-124">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="0a685-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0a685-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a685-125">See also</span></span>

- [<span data-ttu-id="0a685-126">ICorDebugType2 介面</span><span class="sxs-lookup"><span data-stu-id="0a685-126">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
