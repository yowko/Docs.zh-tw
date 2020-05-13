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
ms.openlocfilehash: aac3d54d25b50d0e2ce3e93cdfba5a17679e1f76
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209665"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="545d8-102">ICorDebugProcess5::GetArrayLayout 方法</span><span class="sxs-lookup"><span data-stu-id="545d8-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="545d8-103">提供陣列類型配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="545d8-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="545d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="545d8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="545d8-105">參數</span><span class="sxs-lookup"><span data-stu-id="545d8-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="545d8-106">在[COR_TYPEID](cor-typeid-structure.md) token，指定需要其版面配置的陣列。</span><span class="sxs-lookup"><span data-stu-id="545d8-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="545d8-107">脫銷[COR_ARRAY_LAYOUT](cor-array-layout-structure.md)結構的指標，其中包含記憶體中陣列版面配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="545d8-107">[out] A pointer to a [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="545d8-108">備註</span><span class="sxs-lookup"><span data-stu-id="545d8-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="545d8-109">需求</span><span class="sxs-lookup"><span data-stu-id="545d8-109">Requirements</span></span>  
 <span data-ttu-id="545d8-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="545d8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="545d8-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="545d8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="545d8-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="545d8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="545d8-113">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="545d8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="545d8-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="545d8-114">See also</span></span>

- [<span data-ttu-id="545d8-115">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="545d8-115">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="545d8-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="545d8-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
