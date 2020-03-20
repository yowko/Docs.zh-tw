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
ms.openlocfilehash: 0b210f105495fa3f5595adbcb0805e1d1fb62310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179212"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="991ad-102">CreateCoreClrDebugTarget 函式</span><span class="sxs-lookup"><span data-stu-id="991ad-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="991ad-103">創建與在遠端電腦上運行的調試器代理的連接，並返回一個[ICoreClrDebugTarget](icoreclrdebugtarget-interface.md)物件，該物件可用於查詢遠端電腦上的正在運行的進程和載入的運行時。</span><span class="sxs-lookup"><span data-stu-id="991ad-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="991ad-104">語法</span><span class="sxs-lookup"><span data-stu-id="991ad-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="991ad-105">參數</span><span class="sxs-lookup"><span data-stu-id="991ad-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="991ad-106">[in] 遠端目標電腦的 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="991ad-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="991ad-107">[出]指向將創建的[ICoreClrDebugTarget](icoreclrdebugtarget-interface.md)物件的指標。</span><span class="sxs-lookup"><span data-stu-id="991ad-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="991ad-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="991ad-108">Return Value</span></span>  
 <span data-ttu-id="991ad-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="991ad-109">S_OK</span></span>  
 <span data-ttu-id="991ad-110">已成功確定處理序中的 CLR 數目，並且已正確填入對應的控制代碼和路徑陣列。</span><span class="sxs-lookup"><span data-stu-id="991ad-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="991ad-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="991ad-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="991ad-112">無法為 `ppTarget` 配置足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="991ad-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="991ad-113">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="991ad-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="991ad-114">其他失敗。</span><span class="sxs-lookup"><span data-stu-id="991ad-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="991ad-115">需求</span><span class="sxs-lookup"><span data-stu-id="991ad-115">Requirements</span></span>  
 <span data-ttu-id="991ad-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="991ad-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="991ad-117">**標題：** 核心Clr遠端偵錯介面.h</span><span class="sxs-lookup"><span data-stu-id="991ad-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="991ad-118">**資料庫：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="991ad-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="991ad-119">**.NET 框架版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="991ad-119">**.NET Framework Versions:** 3.5 SP1</span></span>
