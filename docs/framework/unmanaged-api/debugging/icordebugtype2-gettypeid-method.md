---
title: "ICorDebugType2::GetTypeID 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugType2.GetTypeID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30b5259bfd39ac0c8c8b717d59a8d3165f6b6cbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="7dfb5-102">ICorDebugType2::GetTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="7dfb5-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="7dfb5-103">取得[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)此類型。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-103">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dfb5-104">語法</span><span class="sxs-lookup"><span data-stu-id="7dfb5-104">Syntax</span></span>  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7dfb5-105">參數</span><span class="sxs-lookup"><span data-stu-id="7dfb5-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="7dfb5-106">[out]指標[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)此 ICorDebugType 的。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-106">[out] A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7dfb5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="7dfb5-107">Return Value</span></span>  
 <span data-ttu-id="7dfb5-108">如果成功，傳回值為 `S_OK`，如果失敗，則傳回失敗 `HRESULT` 程式碼。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="7dfb5-109">`HRESULT`代碼包括下列：</span><span class="sxs-lookup"><span data-stu-id="7dfb5-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="7dfb5-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="7dfb5-110">Return code</span></span>|<span data-ttu-id="7dfb5-111">描述</span><span class="sxs-lookup"><span data-stu-id="7dfb5-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="7dfb5-112">方法成功。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-112">Method succeeded.</span></span> <span data-ttu-id="7dfb5-113">方法已擷取的有效[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-113">The method has retrieved a valid [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="7dfb5-114">尚未載入的型別。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="7dfb5-115">不支援的類型。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dfb5-116">備註</span><span class="sxs-lookup"><span data-stu-id="7dfb5-116">Remarks</span></span>  
 <span data-ttu-id="7dfb5-117">這個方法從 ICorDebugType，表示類型可能會或可能有尚未載入執行階段中，為提供的對應[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)，這可充當不透明控制代碼識別執行階段中載入的型別。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="7dfb5-118">當 ICorDebugType 代表的類型，尚未已載入，則這個方法會傳回`CORDBG_E_CLASS_NOT_LOADED`。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="7dfb5-119">如果不支援的類型，它會傳回`CORDBG_E_UNSUPPORTED`。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dfb5-120">需求</span><span class="sxs-lookup"><span data-stu-id="7dfb5-120">Requirements</span></span>  
 <span data-ttu-id="7dfb5-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dfb5-122">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7dfb5-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7dfb5-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7dfb5-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7dfb5-124">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dfb5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfb5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dfb5-125">See Also</span></span>  
 [<span data-ttu-id="7dfb5-126">ICorDebugType2 介面</span><span class="sxs-lookup"><span data-stu-id="7dfb5-126">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
