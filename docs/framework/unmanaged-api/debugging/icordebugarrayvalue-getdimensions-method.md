---
title: ICorDebugArrayValue::GetDimensions 方法
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: fa2be894af6e44d09c25a736f45acba56052f9fa
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895045"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="83e63-102">ICorDebugArrayValue::GetDimensions 方法</span><span class="sxs-lookup"><span data-stu-id="83e63-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="83e63-103">取得這個陣列的每個維度中的元素數目。</span><span class="sxs-lookup"><span data-stu-id="83e63-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e63-104">語法</span><span class="sxs-lookup"><span data-stu-id="83e63-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83e63-105">參數</span><span class="sxs-lookup"><span data-stu-id="83e63-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="83e63-106">在這個 ICorDebugArrayValue 物件的維度數目。</span><span class="sxs-lookup"><span data-stu-id="83e63-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="83e63-107">這個值也是`dims`陣列的大小，因為它的大小等於`ICorDebugArrayValue`物件的維度數目。</span><span class="sxs-lookup"><span data-stu-id="83e63-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="83e63-108">脫銷整數的陣列，其中每一個都會指定此`ICorDebugArrayValue`物件中維度內的專案數。</span><span class="sxs-lookup"><span data-stu-id="83e63-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83e63-109">需求</span><span class="sxs-lookup"><span data-stu-id="83e63-109">Requirements</span></span>  
 <span data-ttu-id="83e63-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83e63-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83e63-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83e63-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83e63-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83e63-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83e63-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83e63-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
