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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41a9ff2c94c98a5acc930d68e648b0ea577a82c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492305"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="79424-102">ICorDebugValue::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="79424-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="79424-103">取得大小，以位元組為單位，這個 「 ICorDebugValue 」 物件。</span><span class="sxs-lookup"><span data-stu-id="79424-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79424-104">語法</span><span class="sxs-lookup"><span data-stu-id="79424-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79424-105">參數</span><span class="sxs-lookup"><span data-stu-id="79424-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="79424-106">[out]大小 （位元組），這個值物件。</span><span class="sxs-lookup"><span data-stu-id="79424-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79424-107">備註</span><span class="sxs-lookup"><span data-stu-id="79424-107">Remarks</span></span>  
 <span data-ttu-id="79424-108">如果此值的型別是參考型別，這個方法會傳回指標的大小，而不是物件的大小。</span><span class="sxs-lookup"><span data-stu-id="79424-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="79424-109">`ICorDebugValue::GetSize`方法會傳回`COR_E_OVERFLOW`大於 64 位元平台上為 4 GB 的物件。</span><span class="sxs-lookup"><span data-stu-id="79424-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="79424-110">使用[ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)方法改為物件，會超過 4 GB。</span><span class="sxs-lookup"><span data-stu-id="79424-110">Use the [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79424-111">需求</span><span class="sxs-lookup"><span data-stu-id="79424-111">Requirements</span></span>  
 <span data-ttu-id="79424-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79424-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79424-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79424-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79424-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79424-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79424-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79424-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79424-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79424-116">See also</span></span>

- [<span data-ttu-id="79424-117">GetSize64 方法</span><span class="sxs-lookup"><span data-stu-id="79424-117">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
