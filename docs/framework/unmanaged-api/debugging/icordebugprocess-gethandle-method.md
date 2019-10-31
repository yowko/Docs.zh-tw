---
title: ICorDebugProcess::GetHandle 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
ms.openlocfilehash: e4061580d59b0cf2a6e6e481d5242005e9452caf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128878"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="53cc0-102">ICorDebugProcess::GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="53cc0-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="53cc0-103">取得進程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="53cc0-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53cc0-104">語法</span><span class="sxs-lookup"><span data-stu-id="53cc0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53cc0-105">參數</span><span class="sxs-lookup"><span data-stu-id="53cc0-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="53cc0-106">脫銷指向進程控制碼之 `HPROCESS` 的指標。</span><span class="sxs-lookup"><span data-stu-id="53cc0-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53cc0-107">備註</span><span class="sxs-lookup"><span data-stu-id="53cc0-107">Remarks</span></span>  
 <span data-ttu-id="53cc0-108">抓取的控制碼是由偵錯工具介面所擁有。</span><span class="sxs-lookup"><span data-stu-id="53cc0-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="53cc0-109">偵錯工具在使用之前，應該先複製控制碼。</span><span class="sxs-lookup"><span data-stu-id="53cc0-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53cc0-110">需求</span><span class="sxs-lookup"><span data-stu-id="53cc0-110">Requirements</span></span>  
 <span data-ttu-id="53cc0-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53cc0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53cc0-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53cc0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53cc0-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53cc0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53cc0-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53cc0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
