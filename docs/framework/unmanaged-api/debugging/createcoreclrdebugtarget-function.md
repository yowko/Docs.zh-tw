---
title: CreateCoreClrDebugTarget 函式
ms.date: 03/30/2017
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
ms.openlocfilehash: a7fed8cb70785f0ccfcadf1e16181db303ac98e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789188"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="a9369-102">CreateCoreClrDebugTarget 函式</span><span class="sxs-lookup"><span data-stu-id="a9369-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="a9369-103">建立連接至遠端電腦上執行的偵錯工具 proxy，並傳回可用來查詢執行中進程和載入的執行時間在遠端電腦上的[ICoreClrDebugTarget](icoreclrdebugtarget-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="a9369-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9369-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9369-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9369-105">參數</span><span class="sxs-lookup"><span data-stu-id="a9369-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="a9369-106">[in] 遠端目標電腦的 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="a9369-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="a9369-107">脫銷將建立之[ICoreClrDebugTarget](icoreclrdebugtarget-interface.md)物件指標的指標。</span><span class="sxs-lookup"><span data-stu-id="a9369-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9369-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a9369-108">Return Value</span></span>  
 <span data-ttu-id="a9369-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9369-109">S_OK</span></span>  
 <span data-ttu-id="a9369-110">已成功確定處理序中的 CLR 數目，並且已正確填入對應的控制代碼和路徑陣列。</span><span class="sxs-lookup"><span data-stu-id="a9369-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="a9369-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a9369-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="a9369-112">無法為 `ppTarget` 配置足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a9369-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="a9369-113">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="a9369-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a9369-114">其他失敗。</span><span class="sxs-lookup"><span data-stu-id="a9369-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9369-115">需求</span><span class="sxs-lookup"><span data-stu-id="a9369-115">Requirements</span></span>  
 <span data-ttu-id="a9369-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9369-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9369-117">**標頭：** CoreClrRemoteDebuggingInterfaces。h</span><span class="sxs-lookup"><span data-stu-id="a9369-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="a9369-118">連結**庫：** mscordbi_macx86 .dll</span><span class="sxs-lookup"><span data-stu-id="a9369-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="a9369-119">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a9369-119">**.NET Framework Versions:** 3.5 SP1</span></span>
