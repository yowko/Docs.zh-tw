---
title: ICorDebugProcess3::SetEnableCustomNotification 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
ms.openlocfilehash: 523d9665ffd2637a0e856d74d4d3b3838cb5e83c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212122"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="1797e-102">ICorDebugProcess3::SetEnableCustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="1797e-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="1797e-103">啟用和停用指定類型的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="1797e-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1797e-104">語法</span><span class="sxs-lookup"><span data-stu-id="1797e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1797e-105">參數</span><span class="sxs-lookup"><span data-stu-id="1797e-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="1797e-106">在指定自訂偵錯工具通知的類型。</span><span class="sxs-lookup"><span data-stu-id="1797e-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="1797e-107">[in] `true`若要啟用自訂偵錯工具通知;`false`停用通知。</span><span class="sxs-lookup"><span data-stu-id="1797e-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="1797e-108">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="1797e-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1797e-109">備註</span><span class="sxs-lookup"><span data-stu-id="1797e-109">Remarks</span></span>  
 <span data-ttu-id="1797e-110">當 `fEnable` 設定為時 `true` ，對方法的呼叫會 <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> 觸發[ICorDebugManagedCallback3：： CustomNotification](icordebugmanagedcallback3-customnotification-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="1797e-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="1797e-111">預設會停用通知;因此，偵錯工具必須指定它知道的任何通知類型，並想要處理。</span><span class="sxs-lookup"><span data-stu-id="1797e-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="1797e-112">由於[ICorDebugClass](icordebug-interface.md)類別的範圍是由應用程式域所限定，因此偵錯工具必須 `SetEnableCustomNotification` 針對進程中的每個應用程式域呼叫，如果它想要在整個進程中接收通知。</span><span class="sxs-lookup"><span data-stu-id="1797e-112">Because the [ICorDebugClass](icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="1797e-113">從 .NET Framework 4 開始，唯一支援的通知是跨執行緒相依性通知。</span><span class="sxs-lookup"><span data-stu-id="1797e-113">Starting with the .NET Framework 4, the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1797e-114">需求</span><span class="sxs-lookup"><span data-stu-id="1797e-114">Requirements</span></span>  
 <span data-ttu-id="1797e-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1797e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1797e-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1797e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1797e-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1797e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1797e-118">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1797e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1797e-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="1797e-119">See also</span></span>

- [<span data-ttu-id="1797e-120">ICorDebugProcess3 介面</span><span class="sxs-lookup"><span data-stu-id="1797e-120">ICorDebugProcess3 Interface</span></span>](icordebugprocess3-interface.md)
- [<span data-ttu-id="1797e-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1797e-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1797e-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="1797e-122">Debugging</span></span>](index.md)
