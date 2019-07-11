---
title: ICorDebugArrayValue::GetElement 方法
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 356f7ec9c50ce511883cbf0f5fbcb729493c92af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737578"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="1e28a-102">ICorDebugArrayValue::GetElement 方法</span><span class="sxs-lookup"><span data-stu-id="1e28a-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="1e28a-103">取得指定之陣列元素的值。</span><span class="sxs-lookup"><span data-stu-id="1e28a-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e28a-104">語法</span><span class="sxs-lookup"><span data-stu-id="1e28a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e28a-105">參數</span><span class="sxs-lookup"><span data-stu-id="1e28a-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="1e28a-106">[in]這個維度的數目`ICorDebugArrayValue`物件。</span><span class="sxs-lookup"><span data-stu-id="1e28a-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="1e28a-107">此值也是的大小`indices`因為其大小的維度數目等於陣列`ICorDebugArrayValue`物件。</span><span class="sxs-lookup"><span data-stu-id="1e28a-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="1e28a-108">[in]陣列的索引值，其中每個指定的維度內的位置`ICorDebugArrayValue`物件。</span><span class="sxs-lookup"><span data-stu-id="1e28a-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="1e28a-109">此值不能為 null。</span><span class="sxs-lookup"><span data-stu-id="1e28a-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="1e28a-110">[out]ICorDebugValue 物件，表示指定的項目值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="1e28a-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e28a-111">需求</span><span class="sxs-lookup"><span data-stu-id="1e28a-111">Requirements</span></span>  
 <span data-ttu-id="1e28a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1e28a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e28a-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e28a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e28a-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e28a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e28a-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e28a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
