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
ms.openlocfilehash: 23d68e8e4bbd87779e3b49f0c40f5a5ab9f5124f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617213"
---
# <a name="getcorversion-function"></a><span data-ttu-id="84ad0-102">GetCORVersion 函式</span><span class="sxs-lookup"><span data-stu-id="84ad0-102">GetCORVersion Function</span></span>
<span data-ttu-id="84ad0-103">傳回目前進程中執行之 common language runtime （CLR）的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="84ad0-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="84ad0-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="84ad0-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84ad0-105">語法</span><span class="sxs-lookup"><span data-stu-id="84ad0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="84ad0-106">參數</span><span class="sxs-lookup"><span data-stu-id="84ad0-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="84ad0-107">緩衝區的指標，其中 CLR 會傳回一個字串，指定目前載入進程中的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="84ad0-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="84ad0-108">傳回的字串會採用與傳遞給[CorBindToRuntimeEx](corbindtoruntimeex-function.md)的字串相同的格式，例如 "v 1.0.1216"。</span><span class="sxs-lookup"><span data-stu-id="84ad0-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="84ad0-109">如果執行時間尚未載入進程中，此函式會針對電腦上所安裝的最新執行階段版本，傳回適當的目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="84ad0-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="84ad0-110">`WCHAR`可以保留在中的字元數 `pbuffer` 。</span><span class="sxs-lookup"><span data-stu-id="84ad0-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="84ad0-111">中實際傳回的字元數指標 `pbuffer` 。</span><span class="sxs-lookup"><span data-stu-id="84ad0-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="84ad0-112">如果 `pbuffer` 是 null 指標，執行時間會傳回 E_POINTER。</span><span class="sxs-lookup"><span data-stu-id="84ad0-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="84ad0-113">如果字元數大於的長度，則執行時間會傳回 `pbuffer` ERROR_INSUFFICIENT_BUFFER。</span><span class="sxs-lookup"><span data-stu-id="84ad0-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84ad0-114">需求</span><span class="sxs-lookup"><span data-stu-id="84ad0-114">Requirements</span></span>  
 <span data-ttu-id="84ad0-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84ad0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84ad0-116">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="84ad0-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84ad0-117">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="84ad0-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84ad0-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84ad0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ad0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84ad0-119">See also</span></span>

- [<span data-ttu-id="84ad0-120">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="84ad0-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
