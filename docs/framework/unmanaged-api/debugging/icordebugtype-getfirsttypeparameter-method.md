---
title: ICorDebugType::GetFirstTypeParameter 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
ms.openlocfilehash: be69636056d5510b72dbce39917f5e8d3b05cd87
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723970"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="15438-102">ICorDebugType::GetFirstTypeParameter 方法</span><span class="sxs-lookup"><span data-stu-id="15438-102">ICorDebugType::GetFirstTypeParameter Method</span></span>

<span data-ttu-id="15438-103">取得 ICorDebugType 的介面指標，該指標表示這個所 <xref:System.Type> 表示之型別的第一個參數 `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="15438-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15438-104">語法</span><span class="sxs-lookup"><span data-stu-id="15438-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15438-105">參數</span><span class="sxs-lookup"><span data-stu-id="15438-105">Parameters</span></span>  

 `value`  
 <span data-ttu-id="15438-106">擴展物件位址的指標 `ICorDebugType` ，該物件表示第一個參數。</span><span class="sxs-lookup"><span data-stu-id="15438-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15438-107">備註</span><span class="sxs-lookup"><span data-stu-id="15438-107">Remarks</span></span>  

 <span data-ttu-id="15438-108">`GetFirstTypeParameter` 在類型的其他資訊最多牽涉到一個類型參數的情況下，可以呼叫。</span><span class="sxs-lookup"><span data-stu-id="15438-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="15438-109">尤其是，如果類型是 ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF 或 ELEMENT_TYPE_PTR （如 [ICorDebugType：： GetType](icordebugtype-gettype-method.md) 方法所表示），就可以使用它。</span><span class="sxs-lookup"><span data-stu-id="15438-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15438-110">需求</span><span class="sxs-lookup"><span data-stu-id="15438-110">Requirements</span></span>  

 <span data-ttu-id="15438-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15438-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15438-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15438-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15438-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15438-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15438-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15438-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
