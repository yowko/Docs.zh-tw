---
title: "ICorDebugProcess3::SetEnableCustomNotification 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess3.SetEnableCustomNotification Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ccd1f4b6be56202d5efea1d2e38dce554835218
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="30b34-102">ICorDebugProcess3::SetEnableCustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="30b34-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="30b34-103">啟用和停用指定之類型的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="30b34-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b34-104">語法</span><span class="sxs-lookup"><span data-stu-id="30b34-104">Syntax</span></span>  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30b34-105">參數</span><span class="sxs-lookup"><span data-stu-id="30b34-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="30b34-106">[in]指定自訂偵錯工具通知的型別。</span><span class="sxs-lookup"><span data-stu-id="30b34-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="30b34-107">[in]`true`啟用自訂偵錯工具通知。`false`停用通知。</span><span class="sxs-lookup"><span data-stu-id="30b34-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="30b34-108">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="30b34-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30b34-109">備註</span><span class="sxs-lookup"><span data-stu-id="30b34-109">Remarks</span></span>  
 <span data-ttu-id="30b34-110">當`fEnable`設`true`，呼叫<xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>方法觸發程序[icordebugmanagedcallback3:: Customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="30b34-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="30b34-111">預設值則會停用通知因此，偵錯工具必須指定它知道，而且想要處理的任何通知類型。</span><span class="sxs-lookup"><span data-stu-id="30b34-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="30b34-112">因為[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)範圍類別是由應用程式定義域，偵錯工具必須呼叫`SetEnableCustomNotification`每個應用程式網域中的程序，如果它要接收通知接收之間的整個程序。</span><span class="sxs-lookup"><span data-stu-id="30b34-112">Because the [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="30b34-113">從開始[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]，僅支援的通知是跨執行緒相依性通知。</span><span class="sxs-lookup"><span data-stu-id="30b34-113">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30b34-114">需求</span><span class="sxs-lookup"><span data-stu-id="30b34-114">Requirements</span></span>  
 <span data-ttu-id="30b34-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30b34-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30b34-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30b34-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30b34-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30b34-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30b34-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30b34-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b34-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="30b34-119">See Also</span></span>  
 [<span data-ttu-id="30b34-120">ICorDebugProcess3 介面</span><span class="sxs-lookup"><span data-stu-id="30b34-120">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 [<span data-ttu-id="30b34-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="30b34-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="30b34-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="30b34-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
