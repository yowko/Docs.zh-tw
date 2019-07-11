---
title: ICorDebug::CreateProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d6220270634dd8e2d15787d717020b8f6f86bb9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738324"
---
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="84c6e-102">ICorDebug::CreateProcess 方法</span><span class="sxs-lookup"><span data-stu-id="84c6e-102">ICorDebug::CreateProcess Method</span></span>
<span data-ttu-id="84c6e-103">啟動處理程序和它所控制的偵錯工具的主要執行緒。</span><span class="sxs-lookup"><span data-stu-id="84c6e-103">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84c6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="84c6e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
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
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84c6e-105">參數</span><span class="sxs-lookup"><span data-stu-id="84c6e-105">Parameters</span></span>  
 `lpApplicationName`  
 <span data-ttu-id="84c6e-106">[in]以 null 終止的字串，指定要啟動的程序執行模組的指標。</span><span class="sxs-lookup"><span data-stu-id="84c6e-106">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="84c6e-107">呼叫處理序的安全性內容中執行模組。</span><span class="sxs-lookup"><span data-stu-id="84c6e-107">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="84c6e-108">[in]以 null 終止的字串，指定要啟動的程序執行的命令列的指標。</span><span class="sxs-lookup"><span data-stu-id="84c6e-108">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="84c6e-109">應用程式名稱 (例如，"SomeApp.exe") 必須是第一個引數。</span><span class="sxs-lookup"><span data-stu-id="84c6e-109">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="84c6e-110">[in]Win32 指標`SECURITY_ATTRIBUTES`結構，指定處理程序的安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="84c6e-110">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="84c6e-111">如果`lpProcessAttributes`是 null，此程序取得的預設安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="84c6e-111">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="84c6e-112">[in]Win32 指標`SECURITY_ATTRIBUTES`結構，指定處理程序的主執行緒的安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="84c6e-112">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="84c6e-113">如果`lpThreadAttributes`是 null，執行緒會取得預設安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="84c6e-113">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="84c6e-114">[in]設定為`true`表示啟動的程序，會繼承呼叫處理序中的每個可繼承控制代碼或`false`表示不會繼承控制代碼。</span><span class="sxs-lookup"><span data-stu-id="84c6e-114">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="84c6e-115">繼承的控制代碼具有相同的值與存取權限，原始的控制代碼的形式。</span><span class="sxs-lookup"><span data-stu-id="84c6e-115">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="84c6e-116">[in]位元組合[Win32 處理序建立旗標](https://go.microsoft.com/fwlink/?linkid=69981)，以控制的優先權等級以及啟動的程序的行為。</span><span class="sxs-lookup"><span data-stu-id="84c6e-116">[in] A bitwise combination of the [Win32 Process Creation Flags](https://go.microsoft.com/fwlink/?linkid=69981) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="84c6e-117">[in]新的處理序的環境區塊的指標。</span><span class="sxs-lookup"><span data-stu-id="84c6e-117">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="84c6e-118">[in]以 null 終止的字串，指定處理程序的目前目錄的完整路徑的指標。</span><span class="sxs-lookup"><span data-stu-id="84c6e-118">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="84c6e-119">如果此參數為 null，新處理序會為呼叫處理序有相同的目前磁碟機和目錄。</span><span class="sxs-lookup"><span data-stu-id="84c6e-119">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="84c6e-120">[in]Win32 指標`STARTUPINFOW`結構，指定視窗工作站、 桌面、 標準的控制代碼和啟動的程序的主視窗的外觀。</span><span class="sxs-lookup"><span data-stu-id="84c6e-120">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="84c6e-121">[in]Win32 指標`PROCESS_INFORMATION`結構，指定要啟動的程序的識別資訊。</span><span class="sxs-lookup"><span data-stu-id="84c6e-121">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="84c6e-122">[in]CorDebugCreateProcessFlags 列舉，指定偵錯的選項值。</span><span class="sxs-lookup"><span data-stu-id="84c6e-122">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="84c6e-123">[out]ICorDebugProcess 物件代表處理程序的位址指標。</span><span class="sxs-lookup"><span data-stu-id="84c6e-123">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84c6e-124">備註</span><span class="sxs-lookup"><span data-stu-id="84c6e-124">Remarks</span></span>  
 <span data-ttu-id="84c6e-125">這個方法的參數是一樣的 Win32`CreateProcess`方法。</span><span class="sxs-lookup"><span data-stu-id="84c6e-125">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="84c6e-126">若要啟用非受控的混合模式偵錯，設定`dwCreationFlags`DEBUG_PROCESS 到&#124;DEBUG_ONLY_THIS_PROCESS。</span><span class="sxs-lookup"><span data-stu-id="84c6e-126">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="84c6e-127">如果您想要使用只有 managed 偵錯時，未設定這些旗標。</span><span class="sxs-lookup"><span data-stu-id="84c6e-127">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="84c6e-128">如果要偵錯工具和程序進行偵錯 （附加的處理序） 共用單一主控台中，如果使用 interop 偵錯時，您也可以鎖定主控台，並停止偵錯事件在附加的處理序。</span><span class="sxs-lookup"><span data-stu-id="84c6e-128">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="84c6e-129">偵錯工具就會封鎖任何嘗試使用主控台。</span><span class="sxs-lookup"><span data-stu-id="84c6e-129">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="84c6e-130">若要避免這個問題，請在中設定 CREATE_NEW_CONSOLE 旗標`dwCreationFlags`參數。</span><span class="sxs-lookup"><span data-stu-id="84c6e-130">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="84c6e-131">不支援 Win9x 和非 x86 的平台，例如 IA-64 架構和 amd64 平台的 interop 偵錯。</span><span class="sxs-lookup"><span data-stu-id="84c6e-131">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84c6e-132">需求</span><span class="sxs-lookup"><span data-stu-id="84c6e-132">Requirements</span></span>  
 <span data-ttu-id="84c6e-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84c6e-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84c6e-134">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84c6e-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84c6e-135">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84c6e-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84c6e-136">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84c6e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84c6e-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84c6e-137">See also</span></span>

- [<span data-ttu-id="84c6e-138">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="84c6e-138">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
