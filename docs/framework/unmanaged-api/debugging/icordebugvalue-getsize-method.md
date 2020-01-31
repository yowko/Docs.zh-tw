---
title: ICorDebugValue::GetSize 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
ms.openlocfilehash: 3d26ddb6d89af60acf6dc1214b0423ba75e488ff
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791171"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="652c7-102">ICorDebugValue::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="652c7-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="652c7-103">取得這個 "ICorDebugValue" 物件的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="652c7-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="652c7-104">語法</span><span class="sxs-lookup"><span data-stu-id="652c7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="652c7-105">參數</span><span class="sxs-lookup"><span data-stu-id="652c7-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="652c7-106">脫銷這個值物件的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="652c7-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="652c7-107">備註</span><span class="sxs-lookup"><span data-stu-id="652c7-107">Remarks</span></span>  
 <span data-ttu-id="652c7-108">如果值的類型是參考型別，這個方法會傳回指標的大小，而不是物件的大小。</span><span class="sxs-lookup"><span data-stu-id="652c7-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="652c7-109">`ICorDebugValue::GetSize` 方法會傳回64位平臺上大於 4 GB 之物件的 `COR_E_OVERFLOW`。</span><span class="sxs-lookup"><span data-stu-id="652c7-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="652c7-110">針對大於 4 GB 的物件，請改用[ICorDebugValue3：： GetSize64](icordebugvalue3-getsize64-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="652c7-110">Use the [ICorDebugValue3::GetSize64](icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="652c7-111">需求</span><span class="sxs-lookup"><span data-stu-id="652c7-111">Requirements</span></span>  
 <span data-ttu-id="652c7-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="652c7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="652c7-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="652c7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="652c7-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="652c7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="652c7-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="652c7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="652c7-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="652c7-116">See also</span></span>

- [<span data-ttu-id="652c7-117">GetSize64 方法</span><span class="sxs-lookup"><span data-stu-id="652c7-117">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)
