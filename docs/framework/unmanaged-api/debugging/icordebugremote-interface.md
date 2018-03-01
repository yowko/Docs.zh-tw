---
title: "ICorDebugRemote 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugRemote
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemote
helpviewer_keywords:
- ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: 53d073c6-fa02-40d2-82e1-b9452bb6abaa
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cc34c3a1049a24a27fae4d13288efbd5a98a4dc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="a92cb-102">ICorDebugRemote 介面</span><span class="sxs-lookup"><span data-stu-id="a92cb-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="a92cb-103">提供啟動或附加 Managed 偵錯工具至遠端目標處理序的功能。</span><span class="sxs-lookup"><span data-stu-id="a92cb-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a92cb-104">語法</span><span class="sxs-lookup"><span data-stu-id="a92cb-104">Syntax</span></span>  
  
```  
interface ICorDebugRemote : IUnknown  
{  
    HRESULT CreateProcessEx  
      (  
      [in] ICorDebugRemoteTarget *     pRemoteTarget,  
      [in] LPCWSTR                     lpApplicationName,  
      [in] LPWSTR                      lpCommandLine,  
      [in] LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
      [in] LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
      [in] BOOL                        bInheritHandles,  
      [in] DWORD                       dwCreationFlags,  
      [in] PVOID                       lpEnvironment,  
      [in] LPCWSTR                     lpCurrentDirectory,  
      [in] LPSTARTUPINFOW              lpStartupInfo,  
      [in] LPPROCESS_INFORMATION       lpProcessInformation,  
      [in] CorDebugCreateProcessFlags  debuggingFlags,  
      [out] ICorDebugProcess **        ppProcess  
      );  
  
    HRESULT DebugActiveProcessEx  
      (  
      [in] ICorDebugRemoteTarget *   pRemoteTarget,  
      [in] DWORD                     dwProcessId,  
      [in] BOOL                      fWin32Attach,  
      [out] ICorDebugProcess **      ppProcess  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a92cb-105">方法</span><span class="sxs-lookup"><span data-stu-id="a92cb-105">Methods</span></span>  
  
|<span data-ttu-id="a92cb-106">方法</span><span class="sxs-lookup"><span data-stu-id="a92cb-106">Method</span></span>|<span data-ttu-id="a92cb-107">描述</span><span class="sxs-lookup"><span data-stu-id="a92cb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a92cb-108">ICorDebugRemote::CreateProcessEx 方法</span><span class="sxs-lookup"><span data-stu-id="a92cb-108">ICorDebugRemote::CreateProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-createprocessex-method.md)|<span data-ttu-id="a92cb-109">Managed 偵錯在遠端電腦上建立處理程序。</span><span class="sxs-lookup"><span data-stu-id="a92cb-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="a92cb-110">ICorDebugRemote::DebugActiveProcessEx 方法</span><span class="sxs-lookup"><span data-stu-id="a92cb-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="a92cb-111">啟動處理序在偵錯工具在遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="a92cb-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a92cb-112">備註</span><span class="sxs-lookup"><span data-stu-id="a92cb-112">Remarks</span></span>  
 <span data-ttu-id="a92cb-113">目前，這項功能僅適用於偵錯遠端 Macintosh 電腦執行的 Silverlight 架構應用程式目標支援。</span><span class="sxs-lookup"><span data-stu-id="a92cb-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a92cb-114">需求</span><span class="sxs-lookup"><span data-stu-id="a92cb-114">Requirements</span></span>  
 <span data-ttu-id="a92cb-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a92cb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a92cb-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a92cb-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a92cb-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a92cb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a92cb-118">**.NET framework 版本：** 4.5、 4、 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a92cb-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a92cb-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="a92cb-119">See Also</span></span>  
 [<span data-ttu-id="a92cb-120">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="a92cb-120">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="a92cb-121">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="a92cb-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="a92cb-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a92cb-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
