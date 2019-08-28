---
title: GetCORSystemDirectory 函式
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d30384ea8b9ff4eee41abd43ae39486f770039e7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041430"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="f7621-102">GetCORSystemDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="f7621-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="f7621-103">傳回載入進程的 common language runtime (CLR) 的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="f7621-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="f7621-104">安裝目錄是完整的, 例如 "c:\windows\microsoft.net\framework\v1.0.3705"。</span><span class="sxs-lookup"><span data-stu-id="f7621-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="f7621-105">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="f7621-105">This function is deprecated.</span></span> <span data-ttu-id="f7621-106">它已由 .NET Framework 4 中提供的[ICLRRuntimeInfo:: GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)方法所取代。</span><span class="sxs-lookup"><span data-stu-id="f7621-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7621-107">語法</span><span class="sxs-lookup"><span data-stu-id="f7621-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="f7621-108">參數</span><span class="sxs-lookup"><span data-stu-id="f7621-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="f7621-109">脫銷一個緩衝區, 執行時間會傳回一個字串, 其中包含載入進程之執行時間的完整安裝目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="f7621-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="f7621-110">如果執行時間尚未載入進程中, 此函式會針對電腦上所安裝的最新執行階段版本, 傳回適當的目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="f7621-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f7621-111">在的大小 (以位元組為單位`pbuffer`)。</span><span class="sxs-lookup"><span data-stu-id="f7621-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="f7621-112">脫銷在中`pbuffer`傳回的字元數。</span><span class="sxs-lookup"><span data-stu-id="f7621-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7621-113">備註</span><span class="sxs-lookup"><span data-stu-id="f7621-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f7621-114">請勿在執行 CLR 第4版的進程中使用此函數。</span><span class="sxs-lookup"><span data-stu-id="f7621-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="f7621-115">如果電腦上已安裝舊版的 CLR, 此函式會傳回該版本的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="f7621-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7621-116">需求</span><span class="sxs-lookup"><span data-stu-id="f7621-116">Requirements</span></span>  
 <span data-ttu-id="f7621-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7621-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7621-118">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f7621-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7621-119">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7621-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7621-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7621-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7621-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7621-121">See also</span></span>

- [<span data-ttu-id="f7621-122">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="f7621-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
