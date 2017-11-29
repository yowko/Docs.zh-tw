---
title: "ICorDebug::DebugActiveProcess 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.DebugActiveProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c17345caaec71e4d4b057bdcfc2cc395014cbf82
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="90065-102">ICorDebug::DebugActiveProcess 方法</span><span class="sxs-lookup"><span data-stu-id="90065-102">ICorDebug::DebugActiveProcess Method</span></span>
<span data-ttu-id="90065-103">將偵錯工具附加至現有的處理序。</span><span class="sxs-lookup"><span data-stu-id="90065-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90065-104">語法</span><span class="sxs-lookup"><span data-stu-id="90065-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90065-105">參數</span><span class="sxs-lookup"><span data-stu-id="90065-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="90065-106">[in]是要附加偵錯工具處理序的識別碼。</span><span class="sxs-lookup"><span data-stu-id="90065-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="90065-107">[in]布林值，設為`true`如果偵錯工具時應做為 Win32 偵錯工具處理序的行為及分派 unmanaged 的回呼中; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="90065-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="90065-108">[out]表示要附加偵錯工具的程序的"ICorDebugProcess 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="90065-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90065-109">備註</span><span class="sxs-lookup"><span data-stu-id="90065-109">Remarks</span></span>  
 <span data-ttu-id="90065-110">在 Win9x 和非 x86 平台，例如 IA 64 型和 amd64 平台上不支援 interop 偵錯。</span><span class="sxs-lookup"><span data-stu-id="90065-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90065-111">需求</span><span class="sxs-lookup"><span data-stu-id="90065-111">Requirements</span></span>  
 <span data-ttu-id="90065-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90065-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90065-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90065-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90065-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90065-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90065-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90065-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90065-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90065-116">See Also</span></span>  
 [<span data-ttu-id="90065-117">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="90065-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
