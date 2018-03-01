---
title: "CreateCoreClrDebugTarget 函式"
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
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5b05cc6c84f2f891691613a485d35d008ef79e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="e348f-102">CreateCoreClrDebugTarget 函式</span><span class="sxs-lookup"><span data-stu-id="e348f-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="e348f-103">建立連接至遠端電腦上執行，並傳回偵錯工具 proxy [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)可用來查詢執行的處理序和遠端電腦上載入的執行階段的物件。</span><span class="sxs-lookup"><span data-stu-id="e348f-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e348f-104">語法</span><span class="sxs-lookup"><span data-stu-id="e348f-104">Syntax</span></span>  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e348f-105">參數</span><span class="sxs-lookup"><span data-stu-id="e348f-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="e348f-106">[in] 遠端目標電腦的 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="e348f-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="e348f-107">[out]指標的指標[ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)將建立的物件。</span><span class="sxs-lookup"><span data-stu-id="e348f-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e348f-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e348f-108">Return Value</span></span>  
 <span data-ttu-id="e348f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="e348f-109">S_OK</span></span>  
 <span data-ttu-id="e348f-110">已成功判斷處理序中的 CLR 數目，並且已正確填入對應控制代碼和路徑陣列。</span><span class="sxs-lookup"><span data-stu-id="e348f-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="e348f-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e348f-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="e348f-112">無法為 `ppTarget` 配置足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="e348f-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="e348f-113">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="e348f-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e348f-114">其他失敗。</span><span class="sxs-lookup"><span data-stu-id="e348f-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e348f-115">需求</span><span class="sxs-lookup"><span data-stu-id="e348f-115">Requirements</span></span>  
 <span data-ttu-id="e348f-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e348f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e348f-117">**標頭：** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="e348f-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="e348f-118">**程式庫：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="e348f-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="e348f-119">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="e348f-119">**.NET Framework Versions:** 3.5 SP1</span></span>
