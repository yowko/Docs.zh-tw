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
ms.openlocfilehash: ef11aa48f679592126f736c2877c697f02cb5e62
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379237"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="a2594-102">ICorDebugRemote 介面</span><span class="sxs-lookup"><span data-stu-id="a2594-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="a2594-103">提供啟動或附加 Managed 偵錯工具至遠端目標處理序的功能。</span><span class="sxs-lookup"><span data-stu-id="a2594-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2594-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2594-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="a2594-105">方法</span><span class="sxs-lookup"><span data-stu-id="a2594-105">Methods</span></span>  
  
|<span data-ttu-id="a2594-106">方法</span><span class="sxs-lookup"><span data-stu-id="a2594-106">Method</span></span>|<span data-ttu-id="a2594-107">描述</span><span class="sxs-lookup"><span data-stu-id="a2594-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a2594-108">ICorDebugRemote::CreateProcessEx 方法</span><span class="sxs-lookup"><span data-stu-id="a2594-108">ICorDebugRemote::CreateProcessEx Method</span></span>](icordebugremote-createprocessex-method.md)|<span data-ttu-id="a2594-109">在遠端電腦上建立進程以進行 managed 的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="a2594-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="a2594-110">ICorDebugRemote::DebugActiveProcessEx 方法</span><span class="sxs-lookup"><span data-stu-id="a2594-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="a2594-111">在偵錯工具下的遠端電腦上啟動進程。</span><span class="sxs-lookup"><span data-stu-id="a2594-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2594-112">備註</span><span class="sxs-lookup"><span data-stu-id="a2594-112">Remarks</span></span>  
 <span data-ttu-id="a2594-113">目前，只有針對在遠端 Macintosh 電腦上執行的 Silverlight 應用程式目標進行偵測時，才支援這種功能。</span><span class="sxs-lookup"><span data-stu-id="a2594-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2594-114">需求</span><span class="sxs-lookup"><span data-stu-id="a2594-114">Requirements</span></span>  
 <span data-ttu-id="a2594-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2594-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2594-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2594-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2594-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2594-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2594-118">**.NET Framework 版本：** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a2594-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2594-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="a2594-119">See also</span></span>

- [<span data-ttu-id="a2594-120">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="a2594-120">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="a2594-121">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="a2594-121">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="a2594-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a2594-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
