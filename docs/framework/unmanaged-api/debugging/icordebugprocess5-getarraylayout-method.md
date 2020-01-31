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
ms.openlocfilehash: ea7630efedb7b667dc58174eda0cb98d9f382cfc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792393"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="3e571-102">ICorDebugProcess5::GetArrayLayout 方法</span><span class="sxs-lookup"><span data-stu-id="3e571-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="3e571-103">提供陣列類型配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3e571-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e571-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e571-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e571-105">參數</span><span class="sxs-lookup"><span data-stu-id="3e571-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="3e571-106">在[COR_TYPEID](cor-typeid-structure.md) token，指定需要其版面配置的陣列。</span><span class="sxs-lookup"><span data-stu-id="3e571-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="3e571-107">脫銷[COR_ARRAY_LAYOUT](cor-array-layout-structure.md)結構的指標，其中包含記憶體中陣列版面配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3e571-107">[out] A pointer to a [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e571-108">備註</span><span class="sxs-lookup"><span data-stu-id="3e571-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e571-109">需求</span><span class="sxs-lookup"><span data-stu-id="3e571-109">Requirements</span></span>  
 <span data-ttu-id="3e571-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e571-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e571-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e571-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e571-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e571-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e571-113">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e571-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e571-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="3e571-114">See also</span></span>

- [<span data-ttu-id="3e571-115">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="3e571-115">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="3e571-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3e571-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
