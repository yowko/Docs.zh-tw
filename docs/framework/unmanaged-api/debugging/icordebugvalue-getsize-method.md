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
ms.openlocfilehash: 0023b8ad815b9204ed56791698c7242dfe90bec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421654"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="527a3-102">ICorDebugValue::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="527a3-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="527a3-103">取得大小，以位元組為單位，此 「 ICorDebugValue 」 物件。</span><span class="sxs-lookup"><span data-stu-id="527a3-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="527a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="527a3-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="527a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="527a3-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="527a3-106">[out]以位元組為單位，此值物件的大小。</span><span class="sxs-lookup"><span data-stu-id="527a3-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="527a3-107">備註</span><span class="sxs-lookup"><span data-stu-id="527a3-107">Remarks</span></span>  
 <span data-ttu-id="527a3-108">如果值的類型是參考型別，這個方法會傳回指標的大小，而不是物件的大小。</span><span class="sxs-lookup"><span data-stu-id="527a3-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="527a3-109">`ICorDebugValue::GetSize`方法會傳回`COR_E_OVERFLOW`大於 4 GB，在 64 位元平台上的物件。</span><span class="sxs-lookup"><span data-stu-id="527a3-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="527a3-110">使用[icordebugvalue3:: Getsize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)方法的物件，是大於 4 GB。</span><span class="sxs-lookup"><span data-stu-id="527a3-110">Use the [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="527a3-111">需求</span><span class="sxs-lookup"><span data-stu-id="527a3-111">Requirements</span></span>  
 <span data-ttu-id="527a3-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="527a3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="527a3-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="527a3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="527a3-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="527a3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="527a3-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="527a3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="527a3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="527a3-116">See Also</span></span>  
    
 [<span data-ttu-id="527a3-117">GetSize64 方法</span><span class="sxs-lookup"><span data-stu-id="527a3-117">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
