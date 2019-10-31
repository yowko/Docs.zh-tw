---
title: ICorDebugRemote::CreateProcessEx 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
ms.openlocfilehash: 9e1a5ba65da09c90f33e5e8108c3bd91f3aee4a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131286"
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="ab69e-102">ICorDebugRemote::CreateProcessEx 方法</span><span class="sxs-lookup"><span data-stu-id="ab69e-102">ICorDebugRemote::CreateProcessEx Method</span></span>
<span data-ttu-id="ab69e-103">在偵錯工具下的遠端電腦上啟動進程。</span><span class="sxs-lookup"><span data-stu-id="ab69e-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab69e-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab69e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab69e-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab69e-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="ab69e-106">在[ICorDebugRemoteTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)的指標。</span><span class="sxs-lookup"><span data-stu-id="ab69e-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="ab69e-107">用來判斷將在其上啟動進程的遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="ab69e-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="ab69e-108">在以 null 結束的字串指標，指定啟動的進程所要執行的模組。</span><span class="sxs-lookup"><span data-stu-id="ab69e-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="ab69e-109">模組會在呼叫進程的安全性內容中執行。</span><span class="sxs-lookup"><span data-stu-id="ab69e-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="ab69e-110">在以 null 結束的字串指標，指定啟動的進程所要執行的命令列。</span><span class="sxs-lookup"><span data-stu-id="ab69e-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="ab69e-111">在未使用遠端偵錯程式。</span><span class="sxs-lookup"><span data-stu-id="ab69e-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="ab69e-112">在未使用遠端偵錯程式。</span><span class="sxs-lookup"><span data-stu-id="ab69e-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="ab69e-113">在未使用遠端偵錯程式。</span><span class="sxs-lookup"><span data-stu-id="ab69e-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="ab69e-114">在未使用遠端偵錯程式。</span><span class="sxs-lookup"><span data-stu-id="ab69e-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="ab69e-115">在新進程之環境區塊的指標。</span><span class="sxs-lookup"><span data-stu-id="ab69e-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="ab69e-116">在以 null 結束的字串指標，指定進程目前目錄的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ab69e-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="ab69e-117">如果此參數為 null，新的進程將會具有與呼叫進程相同的目前磁片磁碟機和目錄。</span><span class="sxs-lookup"><span data-stu-id="ab69e-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="ab69e-118">在未使用遠端偵錯程式。</span><span class="sxs-lookup"><span data-stu-id="ab69e-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="ab69e-119">在未使用遠端偵錯程式。</span><span class="sxs-lookup"><span data-stu-id="ab69e-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="ab69e-120">在未使用遠端偵錯程式。</span><span class="sxs-lookup"><span data-stu-id="ab69e-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="ab69e-121">脫銷代表進程之 "ICorDebugProcess Interface" 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="ab69e-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab69e-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="ab69e-122">Return Value</span></span>  
 <span data-ttu-id="ab69e-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="ab69e-123">S_OK</span></span>  
 <span data-ttu-id="ab69e-124">已成功啟動遠端電腦上的進程，並傳回「ICorDebugProcess 介面」以進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ab69e-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="ab69e-125">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="ab69e-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ab69e-126">無法在遠端電腦上啟動進程，並傳回「ICorDebugProcess 介面」以進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ab69e-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab69e-127">備註</span><span class="sxs-lookup"><span data-stu-id="ab69e-127">Remarks</span></span>  
 <span data-ttu-id="ab69e-128">Silverlight 中不支援混合模式的調試。</span><span class="sxs-lookup"><span data-stu-id="ab69e-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab69e-129">需求</span><span class="sxs-lookup"><span data-stu-id="ab69e-129">Requirements</span></span>  
 <span data-ttu-id="ab69e-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab69e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab69e-131">**標頭：** Cordebug.h .idl</span><span class="sxs-lookup"><span data-stu-id="ab69e-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="ab69e-132">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab69e-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab69e-133">**.NET Framework 版本：** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="ab69e-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab69e-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="ab69e-134">See also</span></span>

- [<span data-ttu-id="ab69e-135">ICorDebugRemote 介面</span><span class="sxs-lookup"><span data-stu-id="ab69e-135">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="ab69e-136">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="ab69e-136">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="ab69e-137">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ab69e-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
