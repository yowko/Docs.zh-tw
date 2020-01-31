---
title: ICorDebugThread4::GetCurrentCustomDebuggerNotification 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
ms.openlocfilehash: a8a377074ca1005ad8089dfd8e2a6a464bb86f60
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791359"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="3b478-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification 方法</span><span class="sxs-lookup"><span data-stu-id="3b478-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="3b478-103">取得目前線程上的目前[ICorDebugManagedCallback3：： CustomNotification](icordebugmanagedcallback3-customnotification-method.md)物件。</span><span class="sxs-lookup"><span data-stu-id="3b478-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="3b478-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b478-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="3b478-105">參數</span><span class="sxs-lookup"><span data-stu-id="3b478-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="3b478-106">脫銷目前線程上目前 `ICorDebugManagedCallback3::CustomNotification` 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="3b478-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="3b478-107">備註</span><span class="sxs-lookup"><span data-stu-id="3b478-107">Remarks</span></span>

<span data-ttu-id="3b478-108">如果未從 `ICorDebugManagedCallback3::CustomNotification` 回呼中呼叫方法，或如果沒有目前的通知物件存在，則 `ppNotificationObject` 的值為 null。</span><span class="sxs-lookup"><span data-stu-id="3b478-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="3b478-109">需求</span><span class="sxs-lookup"><span data-stu-id="3b478-109">Requirements</span></span>

<span data-ttu-id="3b478-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b478-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="3b478-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b478-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="3b478-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b478-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3b478-113">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b478-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3b478-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="3b478-114">See also</span></span>

- [<span data-ttu-id="3b478-115">ICorDebugThread4 介面</span><span class="sxs-lookup"><span data-stu-id="3b478-115">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="3b478-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3b478-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3b478-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="3b478-117">Debugging</span></span>](index.md)
