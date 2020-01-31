---
title: ICoreClrDebugTarget 介面
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: 190671b4f690f8c2cad43cf446a1196985ec5a42
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790744"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="94ca1-102">ICoreClrDebugTarget 介面</span><span class="sxs-lookup"><span data-stu-id="94ca1-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="94ca1-103">提供方法來控制參考計數、列舉進程，以及釋放與附加至遠端 Macintosh Silverlight 目標的偵錯工具相關聯的記憶體。</span><span class="sxs-lookup"><span data-stu-id="94ca1-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94ca1-104">語法</span><span class="sxs-lookup"><span data-stu-id="94ca1-104">Syntax</span></span>  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="94ca1-105">方法</span><span class="sxs-lookup"><span data-stu-id="94ca1-105">Methods</span></span>  
  
|<span data-ttu-id="94ca1-106">方法</span><span class="sxs-lookup"><span data-stu-id="94ca1-106">Method</span></span>|<span data-ttu-id="94ca1-107">描述</span><span class="sxs-lookup"><span data-stu-id="94ca1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94ca1-108">ICoreClrDebugTarget::EnumProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="94ca1-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="94ca1-109">列舉在遠端電腦上執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="94ca1-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="94ca1-110">ICoreClrDebugTarget::EnumRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="94ca1-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="94ca1-111">列舉遠端電腦上指定之進程中的 common language runtime （CLRs）。</span><span class="sxs-lookup"><span data-stu-id="94ca1-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="94ca1-112">ICoreClrDebugTarget::FreeMemory 方法</span><span class="sxs-lookup"><span data-stu-id="94ca1-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="94ca1-113">釋放這個類別中的列舉方法所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="94ca1-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94ca1-114">備註</span><span class="sxs-lookup"><span data-stu-id="94ca1-114">Remarks</span></span>  
 <span data-ttu-id="94ca1-115">目前，只有針對在遠端 Macintosh 電腦上執行的 Silverlight 應用程式目標進行偵測時，才支援這種功能。</span><span class="sxs-lookup"><span data-stu-id="94ca1-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94ca1-116">需求</span><span class="sxs-lookup"><span data-stu-id="94ca1-116">Requirements</span></span>  
 <span data-ttu-id="94ca1-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94ca1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94ca1-118">**標頭：** CoreClrRemoteDebuggingInterfaces。h</span><span class="sxs-lookup"><span data-stu-id="94ca1-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="94ca1-119">連結**庫：** mscordbi_macx86 .dll</span><span class="sxs-lookup"><span data-stu-id="94ca1-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="94ca1-120">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="94ca1-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94ca1-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="94ca1-121">See also</span></span>

- [<span data-ttu-id="94ca1-122">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="94ca1-122">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="94ca1-123">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="94ca1-123">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="94ca1-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="94ca1-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
