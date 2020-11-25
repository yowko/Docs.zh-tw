---
title: ICorDebug::DebugActiveProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
ms.openlocfilehash: 1713623fa575bea6df649106b37212f7aeaee6db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723463"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="88460-102">ICorDebug::DebugActiveProcess 方法</span><span class="sxs-lookup"><span data-stu-id="88460-102">ICorDebug::DebugActiveProcess Method</span></span>

<span data-ttu-id="88460-103">將偵錯工具附加至現有的進程。</span><span class="sxs-lookup"><span data-stu-id="88460-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88460-104">語法</span><span class="sxs-lookup"><span data-stu-id="88460-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88460-105">參數</span><span class="sxs-lookup"><span data-stu-id="88460-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="88460-106">在要附加偵錯工具的進程識別碼。</span><span class="sxs-lookup"><span data-stu-id="88460-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="88460-107">在 `true` 如果偵錯工具的行為應該是進程的 Win32 偵錯工具，並分派非受控回呼，則為布林值，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="88460-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="88460-108">擴展"ICorDebugProcess" 物件位址的指標，代表偵錯工具已附加至的進程。</span><span class="sxs-lookup"><span data-stu-id="88460-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88460-109">備註</span><span class="sxs-lookup"><span data-stu-id="88460-109">Remarks</span></span>  

 <span data-ttu-id="88460-110">在 Win9x 和非 x86 平臺上不支援 Interop 偵錯工具，例如 IA-64 型和 AMD64 平臺。</span><span class="sxs-lookup"><span data-stu-id="88460-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88460-111">需求</span><span class="sxs-lookup"><span data-stu-id="88460-111">Requirements</span></span>  

 <span data-ttu-id="88460-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="88460-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88460-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88460-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88460-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88460-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88460-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88460-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88460-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88460-116">See also</span></span>

- [<span data-ttu-id="88460-117">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="88460-117">ICorDebug Interface</span></span>](icordebug-interface.md)
