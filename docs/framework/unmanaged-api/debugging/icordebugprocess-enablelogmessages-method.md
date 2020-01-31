---
title: ICorDebugProcess::EnableLogMessages 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
ms.openlocfilehash: 6b1ccffa4f24122e643a64270f44945afdbc8fff
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792642"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="1b0b3-102">ICorDebugProcess::EnableLogMessages 方法</span><span class="sxs-lookup"><span data-stu-id="1b0b3-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="1b0b3-103">啟用和停用將記錄訊息傳送至偵錯工具的功能。</span><span class="sxs-lookup"><span data-stu-id="1b0b3-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b0b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b0b3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b0b3-105">參數</span><span class="sxs-lookup"><span data-stu-id="1b0b3-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="1b0b3-106">[in] `true` 啟用記錄訊息的傳輸;`false` 會停用傳輸。</span><span class="sxs-lookup"><span data-stu-id="1b0b3-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b0b3-107">備註</span><span class="sxs-lookup"><span data-stu-id="1b0b3-107">Remarks</span></span>  
 <span data-ttu-id="1b0b3-108">只有在發生[ICorDebugManagedCallback：： CreateProcess](icordebugmanagedcallback-createprocess-method.md)回呼之後，這個方法才有效。</span><span class="sxs-lookup"><span data-stu-id="1b0b3-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b0b3-109">需求</span><span class="sxs-lookup"><span data-stu-id="1b0b3-109">Requirements</span></span>  
 <span data-ttu-id="1b0b3-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b0b3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b0b3-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b0b3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b0b3-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b0b3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b0b3-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b0b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
