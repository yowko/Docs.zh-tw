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
ms.openlocfilehash: 0b6b6f46c7fff8f1d4c2ad555c93423f9ca8ac09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698139"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="c8afb-102">ICorDebugArrayValue::GetElement 方法</span><span class="sxs-lookup"><span data-stu-id="c8afb-102">ICorDebugArrayValue::GetElement Method</span></span>

<span data-ttu-id="c8afb-103">取得指定陣列元素的值。</span><span class="sxs-lookup"><span data-stu-id="c8afb-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8afb-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8afb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8afb-105">參數</span><span class="sxs-lookup"><span data-stu-id="c8afb-105">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="c8afb-106">在此物件的維度數目 `ICorDebugArrayValue` 。</span><span class="sxs-lookup"><span data-stu-id="c8afb-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="c8afb-107">此值也是陣列的大小， `indices` 因為其大小等於物件的維度數目 `ICorDebugArrayValue` 。</span><span class="sxs-lookup"><span data-stu-id="c8afb-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="c8afb-108">在索引值的陣列，每個值都會指定物件維度內的位置 `ICorDebugArrayValue` 。</span><span class="sxs-lookup"><span data-stu-id="c8afb-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="c8afb-109">這個值不得為 null。</span><span class="sxs-lookup"><span data-stu-id="c8afb-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c8afb-110">擴展ICorDebugValue 物件位址的指標，該物件表示指定之專案的值。</span><span class="sxs-lookup"><span data-stu-id="c8afb-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8afb-111">需求</span><span class="sxs-lookup"><span data-stu-id="c8afb-111">Requirements</span></span>  

 <span data-ttu-id="c8afb-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8afb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8afb-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8afb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8afb-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8afb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8afb-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8afb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
