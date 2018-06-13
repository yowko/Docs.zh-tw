---
title: ICorDebugProcess5::GetArrayLayout 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e96dccdd2836eebb08e88fe09dda531cd62baeee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419997"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="e54db-102">ICorDebugProcess5::GetArrayLayout 方法</span><span class="sxs-lookup"><span data-stu-id="e54db-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="e54db-103">提供陣列類型的配置資訊。</span><span class="sxs-lookup"><span data-stu-id="e54db-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e54db-104">語法</span><span class="sxs-lookup"><span data-stu-id="e54db-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e54db-105">參數</span><span class="sxs-lookup"><span data-stu-id="e54db-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="e54db-106">[in]A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)語彙基元，指定想要使用的配置的陣列。</span><span class="sxs-lookup"><span data-stu-id="e54db-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="e54db-107">[out]指標[COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)結構，其中包含在記憶體中陣列的配置資訊。</span><span class="sxs-lookup"><span data-stu-id="e54db-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e54db-108">備註</span><span class="sxs-lookup"><span data-stu-id="e54db-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e54db-109">需求</span><span class="sxs-lookup"><span data-stu-id="e54db-109">Requirements</span></span>  
 <span data-ttu-id="e54db-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e54db-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e54db-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e54db-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e54db-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e54db-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e54db-113">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e54db-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e54db-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e54db-114">See Also</span></span>  
 [<span data-ttu-id="e54db-115">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="e54db-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="e54db-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e54db-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
