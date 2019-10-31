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
ms.openlocfilehash: 1283abaf6b08af1d842d8fe4469f7f6c15e38ec5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136427"
---
# <a name="getcorversion-function"></a><span data-ttu-id="d4af8-102">GetCORVersion 函式</span><span class="sxs-lookup"><span data-stu-id="d4af8-102">GetCORVersion Function</span></span>
<span data-ttu-id="d4af8-103">傳回目前進程中執行之 common language runtime （CLR）的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="d4af8-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="d4af8-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="d4af8-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4af8-105">語法</span><span class="sxs-lookup"><span data-stu-id="d4af8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="d4af8-106">參數</span><span class="sxs-lookup"><span data-stu-id="d4af8-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="d4af8-107">緩衝區的指標，其中 CLR 會傳回一個字串，指定目前載入進程中的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="d4af8-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="d4af8-108">傳回的字串會採用與傳遞給[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)的字串相同的格式，例如 "v 1.0.1216"。</span><span class="sxs-lookup"><span data-stu-id="d4af8-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="d4af8-109">如果執行時間尚未載入進程中，此函式會針對電腦上所安裝的最新執行階段版本，傳回適當的目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="d4af8-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="d4af8-110">可保留在 `pbuffer`中的字元數（`WCHAR`秒）。</span><span class="sxs-lookup"><span data-stu-id="d4af8-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="d4af8-111">`pbuffer`中實際傳回的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="d4af8-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="d4af8-112">如果 `pbuffer` 是 null 指標，則執行時間會傳回 E_POINTER。</span><span class="sxs-lookup"><span data-stu-id="d4af8-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="d4af8-113">如果字元數大於 `pbuffer` 的長度，則執行時間會傳回 ERROR_INSUFFICIENT_BUFFER。</span><span class="sxs-lookup"><span data-stu-id="d4af8-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4af8-114">需求</span><span class="sxs-lookup"><span data-stu-id="d4af8-114">Requirements</span></span>  
 <span data-ttu-id="d4af8-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4af8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4af8-116">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="d4af8-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4af8-117">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="d4af8-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4af8-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4af8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4af8-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="d4af8-119">See also</span></span>

- [<span data-ttu-id="d4af8-120">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="d4af8-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
