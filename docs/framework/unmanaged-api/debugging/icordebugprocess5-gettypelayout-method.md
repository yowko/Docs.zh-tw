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
ms.openlocfilehash: 16da3948d89febc12a72ef54fbc060689a3964c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423243"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="34a74-102">ICorDebugProcess5::GetTypeLayout 方法</span><span class="sxs-lookup"><span data-stu-id="34a74-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="34a74-103">根據其類型識別項的記憶體中取得物件的配置資訊。</span><span class="sxs-lookup"><span data-stu-id="34a74-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34a74-104">語法</span><span class="sxs-lookup"><span data-stu-id="34a74-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34a74-105">參數</span><span class="sxs-lookup"><span data-stu-id="34a74-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="34a74-106">[in]A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)指定想要使用的配置類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="34a74-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="34a74-107">[out]指標[COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)結構，其中包含配置資訊的記憶體中的物件。</span><span class="sxs-lookup"><span data-stu-id="34a74-107">[out] A pointer to a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34a74-108">備註</span><span class="sxs-lookup"><span data-stu-id="34a74-108">Remarks</span></span>  
 <span data-ttu-id="34a74-109">`ICorDebugProcess5::GetTypeLayout`方法提供根據某物件的相關資訊及其[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)，傳回由數項其他[ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)方法。</span><span class="sxs-lookup"><span data-stu-id="34a74-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="34a74-110">所提供的資訊[COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)填入方法的結構。</span><span class="sxs-lookup"><span data-stu-id="34a74-110">The information is provided by a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34a74-111">需求</span><span class="sxs-lookup"><span data-stu-id="34a74-111">Requirements</span></span>  
 <span data-ttu-id="34a74-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="34a74-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34a74-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34a74-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34a74-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34a74-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34a74-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34a74-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34a74-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34a74-116">See Also</span></span>  
 [<span data-ttu-id="34a74-117">COR_TYPE_LAYOUT 結構</span><span class="sxs-lookup"><span data-stu-id="34a74-117">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 [<span data-ttu-id="34a74-118">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="34a74-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="34a74-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="34a74-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
