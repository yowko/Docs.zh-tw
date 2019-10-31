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
ms.openlocfilehash: 3d45caae56403d77776f1a8adbb5fb9c368ff105
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088497"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="a5d71-102">ICorDebugArrayValue::GetElement 方法</span><span class="sxs-lookup"><span data-stu-id="a5d71-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="a5d71-103">取得給定陣列元素的值。</span><span class="sxs-lookup"><span data-stu-id="a5d71-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5d71-104">語法</span><span class="sxs-lookup"><span data-stu-id="a5d71-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5d71-105">參數</span><span class="sxs-lookup"><span data-stu-id="a5d71-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="a5d71-106">在這個 `ICorDebugArrayValue` 物件的維度數目。</span><span class="sxs-lookup"><span data-stu-id="a5d71-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="a5d71-107">這個值也是 `indices` 陣列的大小，因為它的大小等於 `ICorDebugArrayValue` 物件的維度數目。</span><span class="sxs-lookup"><span data-stu-id="a5d71-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="a5d71-108">在索引值的陣列，其中每一個都指定 `ICorDebugArrayValue` 物件之維度中的位置。</span><span class="sxs-lookup"><span data-stu-id="a5d71-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="a5d71-109">此值不得為 null。</span><span class="sxs-lookup"><span data-stu-id="a5d71-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a5d71-110">脫銷ICorDebugValue 物件位址的指標，表示指定元素的值。</span><span class="sxs-lookup"><span data-stu-id="a5d71-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5d71-111">需求</span><span class="sxs-lookup"><span data-stu-id="a5d71-111">Requirements</span></span>  
 <span data-ttu-id="a5d71-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5d71-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5d71-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5d71-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5d71-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5d71-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5d71-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5d71-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
