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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a84061cff7cc5dbdeba1e0e66396e04a8f345cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423152"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="9b4e7-102">ICorDebugProcess3::SetEnableCustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="9b4e7-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="9b4e7-103">啟用和停用指定之類型的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="9b4e7-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b4e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b4e7-104">Syntax</span></span>  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b4e7-105">參數</span><span class="sxs-lookup"><span data-stu-id="9b4e7-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="9b4e7-106">[in]指定自訂偵錯工具通知的型別。</span><span class="sxs-lookup"><span data-stu-id="9b4e7-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="9b4e7-107">[in]`true`啟用自訂偵錯工具通知。`false`停用通知。</span><span class="sxs-lookup"><span data-stu-id="9b4e7-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="9b4e7-108">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="9b4e7-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b4e7-109">備註</span><span class="sxs-lookup"><span data-stu-id="9b4e7-109">Remarks</span></span>  
 <span data-ttu-id="9b4e7-110">當`fEnable`設`true`，呼叫<xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>方法觸發程序[icordebugmanagedcallback3:: Customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="9b4e7-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="9b4e7-111">預設值則會停用通知因此，偵錯工具必須指定它知道，而且想要處理的任何通知類型。</span><span class="sxs-lookup"><span data-stu-id="9b4e7-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="9b4e7-112">因為[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)範圍類別是由應用程式定義域，偵錯工具必須呼叫`SetEnableCustomNotification`每個應用程式網域中的程序，如果它要接收通知接收之間的整個程序。</span><span class="sxs-lookup"><span data-stu-id="9b4e7-112">Because the [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="9b4e7-113">從開始[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]，僅支援的通知是跨執行緒相依性通知。</span><span class="sxs-lookup"><span data-stu-id="9b4e7-113">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b4e7-114">需求</span><span class="sxs-lookup"><span data-stu-id="9b4e7-114">Requirements</span></span>  
 <span data-ttu-id="9b4e7-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b4e7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b4e7-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b4e7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b4e7-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b4e7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b4e7-118">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b4e7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b4e7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b4e7-119">See Also</span></span>  
 [<span data-ttu-id="9b4e7-120">ICorDebugProcess3 介面</span><span class="sxs-lookup"><span data-stu-id="9b4e7-120">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 [<span data-ttu-id="9b4e7-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9b4e7-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9b4e7-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="9b4e7-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
