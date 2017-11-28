---
title: "ICorDebugManagedCallback::Exception 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 550b4961cb082ca6ee745b1d998a6fa95a22ace3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="91de8-102">ICorDebugManagedCallback::Exception 方法</span><span class="sxs-lookup"><span data-stu-id="91de8-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="91de8-103">例外狀況已擲回從 managed 程式碼會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="91de8-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91de8-104">語法</span><span class="sxs-lookup"><span data-stu-id="91de8-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91de8-105">參數</span><span class="sxs-lookup"><span data-stu-id="91de8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="91de8-106">[in]表示擲回例外狀況所在的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="91de8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="91de8-107">[in]表示擲回例外狀況所在的執行緒 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="91de8-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="91de8-108">[in]如果此值為`false`、 例外狀況尚未已由應用程式處理，否則，例外狀況未經處理，並將會終止處理程序。</span><span class="sxs-lookup"><span data-stu-id="91de8-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91de8-109">備註</span><span class="sxs-lookup"><span data-stu-id="91de8-109">Remarks</span></span>  
 <span data-ttu-id="91de8-110">從執行緒物件，可以擷取該特定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="91de8-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91de8-111">需求</span><span class="sxs-lookup"><span data-stu-id="91de8-111">Requirements</span></span>  
 <span data-ttu-id="91de8-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91de8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91de8-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91de8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91de8-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91de8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91de8-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91de8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91de8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91de8-116">See Also</span></span>  
 [<span data-ttu-id="91de8-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="91de8-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
