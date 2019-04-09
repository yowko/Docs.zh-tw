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
ms.openlocfilehash: 332de11790e78b712a429365bd89cc9e41539edc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105517"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="70e50-102">ICorDebugProcess5::GetArrayLayout 方法</span><span class="sxs-lookup"><span data-stu-id="70e50-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="70e50-103">提供關於版面配置的陣列類型的資訊。</span><span class="sxs-lookup"><span data-stu-id="70e50-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70e50-104">語法</span><span class="sxs-lookup"><span data-stu-id="70e50-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70e50-105">參數</span><span class="sxs-lookup"><span data-stu-id="70e50-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="70e50-106">[in]A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)語彙基元，指定想要使用的配置的陣列。</span><span class="sxs-lookup"><span data-stu-id="70e50-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="70e50-107">[out]指標[COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)結構，包含在記憶體中陣列的版面配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="70e50-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70e50-108">備註</span><span class="sxs-lookup"><span data-stu-id="70e50-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70e50-109">需求</span><span class="sxs-lookup"><span data-stu-id="70e50-109">Requirements</span></span>  
 <span data-ttu-id="70e50-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70e50-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70e50-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70e50-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70e50-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70e50-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="70e50-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="70e50-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="70e50-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70e50-114">See also</span></span>

- [<span data-ttu-id="70e50-115">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="70e50-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="70e50-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="70e50-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
