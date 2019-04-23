---
title: GetCORVersion 函式
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f66e00c3334aecdf8c653f57e28d1b327c4170e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094049"
---
# <a name="getcorversion-function"></a><span data-ttu-id="522f6-102">GetCORVersion 函式</span><span class="sxs-lookup"><span data-stu-id="522f6-102">GetCORVersion Function</span></span>
<span data-ttu-id="522f6-103">傳回 common language runtime (CLR) 在目前的處理序中執行的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="522f6-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="522f6-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="522f6-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="522f6-105">語法</span><span class="sxs-lookup"><span data-stu-id="522f6-105">Syntax</span></span>  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="522f6-106">參數</span><span class="sxs-lookup"><span data-stu-id="522f6-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="522f6-107">CLR 會傳回字串，指定目前已載入到處理序的執行階段版本的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="522f6-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="522f6-108">傳回的字串會採用相同的格式字串傳遞至[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)，例如"v1.0.1216 」。</span><span class="sxs-lookup"><span data-stu-id="522f6-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="522f6-109">如果執行階段尚未載入到處理序，則函數會傳回最新版本的執行階段電腦上安裝適當的目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="522f6-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="522f6-110">字元數 (`WCHAR`s)，可以保留在`pbuffer`。</span><span class="sxs-lookup"><span data-stu-id="522f6-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="522f6-111">中實際傳回的字元數的指標`pbuffer`。</span><span class="sxs-lookup"><span data-stu-id="522f6-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="522f6-112">如果`pbuffer`為 null 指標，執行階段傳回 E_POINTER。</span><span class="sxs-lookup"><span data-stu-id="522f6-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="522f6-113">如果字元數大於的長度`pbuffer`，執行階段會傳回 ERROR_INSUFFICIENT_BUFFER。</span><span class="sxs-lookup"><span data-stu-id="522f6-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="522f6-114">需求</span><span class="sxs-lookup"><span data-stu-id="522f6-114">Requirements</span></span>  
 <span data-ttu-id="522f6-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="522f6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="522f6-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="522f6-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="522f6-117">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="522f6-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="522f6-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="522f6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="522f6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="522f6-119">See also</span></span>

- [<span data-ttu-id="522f6-120">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="522f6-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
