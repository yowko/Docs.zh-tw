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
ms.openlocfilehash: 76ad1c0ac421f05cf30f6d3d1f3e65848796a0c7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378702"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="93007-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification 方法</span><span class="sxs-lookup"><span data-stu-id="93007-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="93007-103">取得目前線程上的目前[ICorDebugManagedCallback3：： CustomNotification](icordebugmanagedcallback3-customnotification-method.md)物件。</span><span class="sxs-lookup"><span data-stu-id="93007-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="93007-104">語法</span><span class="sxs-lookup"><span data-stu-id="93007-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="93007-105">參數</span><span class="sxs-lookup"><span data-stu-id="93007-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="93007-106">脫銷`ICorDebugManagedCallback3::CustomNotification`目前線程上目前物件的指標。</span><span class="sxs-lookup"><span data-stu-id="93007-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="93007-107">備註</span><span class="sxs-lookup"><span data-stu-id="93007-107">Remarks</span></span>

<span data-ttu-id="93007-108">`ppNotificationObject`如果不是從回呼內呼叫方法 `ICorDebugManagedCallback3::CustomNotification` ，或如果沒有目前的通知物件存在，則的值會是 null。</span><span class="sxs-lookup"><span data-stu-id="93007-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="93007-109">需求</span><span class="sxs-lookup"><span data-stu-id="93007-109">Requirements</span></span>

<span data-ttu-id="93007-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93007-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="93007-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93007-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="93007-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93007-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="93007-113">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93007-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="93007-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="93007-114">See also</span></span>

- [<span data-ttu-id="93007-115">ICorDebugThread4 介面</span><span class="sxs-lookup"><span data-stu-id="93007-115">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="93007-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="93007-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="93007-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="93007-117">Debugging</span></span>](index.md)
