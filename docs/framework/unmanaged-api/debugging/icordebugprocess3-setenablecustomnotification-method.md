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
ms.openlocfilehash: f2f365f3fe1568f2dd3bad677dd77a13946002e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792471"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="3ff48-102">ICorDebugProcess3::SetEnableCustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="3ff48-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="3ff48-103">啟用和停用指定類型的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="3ff48-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ff48-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ff48-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ff48-105">參數</span><span class="sxs-lookup"><span data-stu-id="3ff48-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="3ff48-106">在指定自訂偵錯工具通知的類型。</span><span class="sxs-lookup"><span data-stu-id="3ff48-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="3ff48-107">[in] `true` 啟用自訂偵錯工具通知;`false` 停用通知。</span><span class="sxs-lookup"><span data-stu-id="3ff48-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="3ff48-108">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3ff48-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ff48-109">備註</span><span class="sxs-lookup"><span data-stu-id="3ff48-109">Remarks</span></span>  
 <span data-ttu-id="3ff48-110">當 `fEnable` 設定為 `true`時，對 <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> 方法的呼叫會觸發[ICorDebugManagedCallback3：： CustomNotification](icordebugmanagedcallback3-customnotification-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="3ff48-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="3ff48-111">預設會停用通知;因此，偵錯工具必須指定它知道的任何通知類型，並想要處理。</span><span class="sxs-lookup"><span data-stu-id="3ff48-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="3ff48-112">由於[ICorDebugClass](icordebug-interface.md)類別的範圍是由應用程式域所限定，因此偵錯工具必須針對進程中的每個應用程式域呼叫 `SetEnableCustomNotification` （如果它想要在整個進程中接收通知）。</span><span class="sxs-lookup"><span data-stu-id="3ff48-112">Because the [ICorDebugClass](icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="3ff48-113">從 .NET Framework 4 開始，唯一支援的通知是跨執行緒相依性通知。</span><span class="sxs-lookup"><span data-stu-id="3ff48-113">Starting with the .NET Framework 4, the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ff48-114">需求</span><span class="sxs-lookup"><span data-stu-id="3ff48-114">Requirements</span></span>  
 <span data-ttu-id="3ff48-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ff48-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ff48-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ff48-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ff48-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ff48-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ff48-118">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ff48-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ff48-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="3ff48-119">See also</span></span>

- [<span data-ttu-id="3ff48-120">ICorDebugProcess3 介面</span><span class="sxs-lookup"><span data-stu-id="3ff48-120">ICorDebugProcess3 Interface</span></span>](icordebugprocess3-interface.md)
- [<span data-ttu-id="3ff48-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3ff48-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3ff48-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="3ff48-122">Debugging</span></span>](index.md)
