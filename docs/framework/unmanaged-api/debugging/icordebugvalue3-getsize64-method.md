---
title: ICorDebugValue3::GetSize64 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
ms.openlocfilehash: d1d057d38e16503175138c6ec978eb6c1f12bc6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722332"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="343e6-102">ICorDebugValue3::GetSize64 方法</span><span class="sxs-lookup"><span data-stu-id="343e6-102">ICorDebugValue3::GetSize64 Method</span></span>

<span data-ttu-id="343e6-103">取得這個 [ICorDebugValue3](icordebugvalue3-interface.md) 物件的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="343e6-103">Gets the size, in bytes, of this [ICorDebugValue3](icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="343e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="343e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="343e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="343e6-105">Parameters</span></span>  

 <span data-ttu-id="343e6-106">pSize</span><span class="sxs-lookup"><span data-stu-id="343e6-106">pSize</span></span>  
 <span data-ttu-id="343e6-107">擴展這個物件的大小指標，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="343e6-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="343e6-108">備註</span><span class="sxs-lookup"><span data-stu-id="343e6-108">Remarks</span></span>  

 <span data-ttu-id="343e6-109">如果這個值的型別是參考型別，這個方法會傳回指標的大小，而不是物件的大小。</span><span class="sxs-lookup"><span data-stu-id="343e6-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="343e6-110">`ICorDebugValue3::GetSize`方法與其 output 參數類型中的[ICorDebugValue：： GetSize](icordebugvalue-getsize-method.md)方法不同。</span><span class="sxs-lookup"><span data-stu-id="343e6-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="343e6-111">在 [ICorDebugValue：： GetSize](icordebugvalue-getsize-method.md)中，output 參數是的 `ULONG32` `ICorDebugValue3::GetSize` ，它是 `ULONG64` 。</span><span class="sxs-lookup"><span data-stu-id="343e6-111">In [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="343e6-112">這可讓 [ICorDebugValue3](icordebugvalue3-interface.md) 介面報告超過2gb 的陣列大小。</span><span class="sxs-lookup"><span data-stu-id="343e6-112">This enables the [ICorDebugValue3](icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="343e6-113">需求</span><span class="sxs-lookup"><span data-stu-id="343e6-113">Requirements</span></span>  

 <span data-ttu-id="343e6-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="343e6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="343e6-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="343e6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="343e6-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="343e6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="343e6-117">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="343e6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="343e6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="343e6-118">See also</span></span>

- [<span data-ttu-id="343e6-119">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="343e6-119">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="343e6-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="343e6-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
