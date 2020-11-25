---
title: ICorDebugRemote::DebugActiveProcessEx 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
ms.openlocfilehash: c9847fd6122aa32c95aecd5643a62a6775ae38d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712114"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="41e5c-102">ICorDebugRemote::DebugActiveProcessEx 方法</span><span class="sxs-lookup"><span data-stu-id="41e5c-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>

<span data-ttu-id="41e5c-103">在偵錯工具下啟動遠端電腦上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="41e5c-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e5c-104">語法</span><span class="sxs-lookup"><span data-stu-id="41e5c-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41e5c-105">參數</span><span class="sxs-lookup"><span data-stu-id="41e5c-105">Parameters</span></span>  

 `pRemoteTarget`  
 <span data-ttu-id="41e5c-106">在 [ICorDebugRemoteTarget 介面](icordebugremotetarget-interface.md)的指標。</span><span class="sxs-lookup"><span data-stu-id="41e5c-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="41e5c-107">這個參數是用來判斷正在執行進程的電腦。</span><span class="sxs-lookup"><span data-stu-id="41e5c-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="41e5c-108">在要附加偵錯工具的進程識別碼。</span><span class="sxs-lookup"><span data-stu-id="41e5c-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="41e5c-109">[in] `true` 如果偵錯工具的行為應該是進程的 Win32 偵錯工具，並分派非受控回呼;否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="41e5c-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="41e5c-110">擴展"ICorDebugProcess" 物件位址的指標，代表偵錯工具已附加至的進程。</span><span class="sxs-lookup"><span data-stu-id="41e5c-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41e5c-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="41e5c-111">Return Value</span></span>  

 <span data-ttu-id="41e5c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="41e5c-112">S_OK</span></span>  
 <span data-ttu-id="41e5c-113">已成功附加至遠端電腦上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="41e5c-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="41e5c-114">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="41e5c-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="41e5c-115">無法連接到遠端電腦上的進程。</span><span class="sxs-lookup"><span data-stu-id="41e5c-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41e5c-116">備註</span><span class="sxs-lookup"><span data-stu-id="41e5c-116">Remarks</span></span>  

 <span data-ttu-id="41e5c-117">Silverlight 不支援混合模式的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="41e5c-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41e5c-118">需求</span><span class="sxs-lookup"><span data-stu-id="41e5c-118">Requirements</span></span>  

 <span data-ttu-id="41e5c-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41e5c-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41e5c-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41e5c-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41e5c-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41e5c-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41e5c-122">**.NET Framework 版本：** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="41e5c-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e5c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41e5c-123">See also</span></span>

- [<span data-ttu-id="41e5c-124">ICorDebugRemote 介面</span><span class="sxs-lookup"><span data-stu-id="41e5c-124">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="41e5c-125">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="41e5c-125">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="41e5c-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="41e5c-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
