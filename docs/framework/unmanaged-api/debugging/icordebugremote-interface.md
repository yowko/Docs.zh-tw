---
title: ICorDebugRemote 介面
ms.date: 03/30/2017
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
ms.openlocfilehash: 276d36c511105087190cb7e9dfeaa6932efc67ff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712101"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="204c2-102">ICorDebugRemote 介面</span><span class="sxs-lookup"><span data-stu-id="204c2-102">ICorDebugRemote Interface</span></span>

<span data-ttu-id="204c2-103">提供啟動或附加 Managed 偵錯工具至遠端目標處理序的功能。</span><span class="sxs-lookup"><span data-stu-id="204c2-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="204c2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="204c2-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="methods"></a><span data-ttu-id="204c2-105">方法</span><span class="sxs-lookup"><span data-stu-id="204c2-105">Methods</span></span>  
  
|<span data-ttu-id="204c2-106">方法</span><span class="sxs-lookup"><span data-stu-id="204c2-106">Method</span></span>|<span data-ttu-id="204c2-107">描述</span><span class="sxs-lookup"><span data-stu-id="204c2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="204c2-108">ICorDebugRemote::CreateProcessEx 方法</span><span class="sxs-lookup"><span data-stu-id="204c2-108">ICorDebugRemote::CreateProcessEx Method</span></span>](icordebugremote-createprocessex-method.md)|<span data-ttu-id="204c2-109">在遠端電腦上建立處理 managed 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="204c2-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="204c2-110">ICorDebugRemote::DebugActiveProcessEx 方法</span><span class="sxs-lookup"><span data-stu-id="204c2-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="204c2-111">在偵錯工具下啟動遠端電腦上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="204c2-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="204c2-112">備註</span><span class="sxs-lookup"><span data-stu-id="204c2-112">Remarks</span></span>  

 <span data-ttu-id="204c2-113">目前，只有在遠端 Macintosh 電腦上執行的 Silverlight 應用程式目標進行偵錯工具時，才支援這項功能。</span><span class="sxs-lookup"><span data-stu-id="204c2-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="204c2-114">需求</span><span class="sxs-lookup"><span data-stu-id="204c2-114">Requirements</span></span>  

 <span data-ttu-id="204c2-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="204c2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="204c2-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="204c2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="204c2-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="204c2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="204c2-118">**.NET Framework 版本：** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="204c2-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="204c2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="204c2-119">See also</span></span>

- [<span data-ttu-id="204c2-120">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="204c2-120">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="204c2-121">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="204c2-121">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="204c2-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="204c2-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
