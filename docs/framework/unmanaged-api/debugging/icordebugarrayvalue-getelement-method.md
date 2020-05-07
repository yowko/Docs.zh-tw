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
ms.openlocfilehash: 7a52e61f41bd1d7f68523dd16f70010ffbba401e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895027"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="e8303-102">ICorDebugArrayValue::GetElement 方法</span><span class="sxs-lookup"><span data-stu-id="e8303-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="e8303-103">取得給定陣列元素的值。</span><span class="sxs-lookup"><span data-stu-id="e8303-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8303-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8303-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8303-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8303-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="e8303-106">在這個`ICorDebugArrayValue`物件的維度數目。</span><span class="sxs-lookup"><span data-stu-id="e8303-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="e8303-107">這個值也是`indices`陣列的大小，因為它的大小等於`ICorDebugArrayValue`物件的維度數目。</span><span class="sxs-lookup"><span data-stu-id="e8303-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="e8303-108">在索引值的陣列，其中每一個都會指定`ICorDebugArrayValue`物件維度內的位置。</span><span class="sxs-lookup"><span data-stu-id="e8303-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="e8303-109">此值不得為 null。</span><span class="sxs-lookup"><span data-stu-id="e8303-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="e8303-110">脫銷ICorDebugValue 物件位址的指標，表示指定元素的值。</span><span class="sxs-lookup"><span data-stu-id="e8303-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8303-111">需求</span><span class="sxs-lookup"><span data-stu-id="e8303-111">Requirements</span></span>  
 <span data-ttu-id="e8303-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8303-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8303-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8303-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8303-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8303-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8303-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8303-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
