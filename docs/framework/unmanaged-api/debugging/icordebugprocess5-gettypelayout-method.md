---
title: ICorDebugProcess5::GetTypeLayout 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee556f559a7dc4c271f110f7bba4c86b675c3511
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736501"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="e89bd-102">ICorDebugProcess5::GetTypeLayout 方法</span><span class="sxs-lookup"><span data-stu-id="e89bd-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="e89bd-103">取得根據其型別識別項的記憶體中的物件配置資訊。</span><span class="sxs-lookup"><span data-stu-id="e89bd-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e89bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="e89bd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e89bd-105">參數</span><span class="sxs-lookup"><span data-stu-id="e89bd-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="e89bd-106">[in]A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)指定想要使用的配置類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e89bd-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="e89bd-107">[out]指標[COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)結構，包含記憶體中的物件配置資訊。</span><span class="sxs-lookup"><span data-stu-id="e89bd-107">[out] A pointer to a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e89bd-108">備註</span><span class="sxs-lookup"><span data-stu-id="e89bd-108">Remarks</span></span>  
 <span data-ttu-id="e89bd-109">`ICorDebugProcess5::GetTypeLayout`方法會提供根據物件的相關資訊及其[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)，所傳回的其他一些[ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e89bd-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="e89bd-110">所提供的資訊[COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)填入方法的結構。</span><span class="sxs-lookup"><span data-stu-id="e89bd-110">The information is provided by a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e89bd-111">需求</span><span class="sxs-lookup"><span data-stu-id="e89bd-111">Requirements</span></span>  
 <span data-ttu-id="e89bd-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e89bd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e89bd-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e89bd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e89bd-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e89bd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e89bd-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e89bd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e89bd-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e89bd-116">See also</span></span>

- [<span data-ttu-id="e89bd-117">COR_TYPE_LAYOUT 結構</span><span class="sxs-lookup"><span data-stu-id="e89bd-117">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)
- [<span data-ttu-id="e89bd-118">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="e89bd-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="e89bd-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e89bd-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
