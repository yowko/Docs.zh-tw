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
ms.openlocfilehash: 1f40f27651d2d75cf2c3e4d7d1c21e1f47d402af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178196"
---
# <a name="getcorversion-function"></a><span data-ttu-id="96a55-102">GetCORVersion 函式</span><span class="sxs-lookup"><span data-stu-id="96a55-102">GetCORVersion Function</span></span>
<span data-ttu-id="96a55-103">返回當前進程中運行的通用語言運行時 （CLR） 的版本號。</span><span class="sxs-lookup"><span data-stu-id="96a55-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="96a55-104">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="96a55-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96a55-105">語法</span><span class="sxs-lookup"><span data-stu-id="96a55-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="96a55-106">參數</span><span class="sxs-lookup"><span data-stu-id="96a55-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="96a55-107">指向緩衝區的指標，其中 CLR 返回一個字串，指定當前載入到進程的運行時的版本。</span><span class="sxs-lookup"><span data-stu-id="96a55-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="96a55-108">返回的字串採用與傳遞給[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)的字串相同的形式，例如"v1.0.1216"。</span><span class="sxs-lookup"><span data-stu-id="96a55-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="96a55-109">如果運行時尚未載入到進程中，該函數將返回電腦上安裝的最新版本的運行時的相應目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="96a55-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="96a55-110">可在 中`pbuffer`持有的字元`WCHAR`數 。</span><span class="sxs-lookup"><span data-stu-id="96a55-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="96a55-111">指向 中`pbuffer`實際返回的字元數的指標。</span><span class="sxs-lookup"><span data-stu-id="96a55-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="96a55-112">如果`pbuffer`為空指標，則運行時返回E_POINTER。</span><span class="sxs-lookup"><span data-stu-id="96a55-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="96a55-113">如果字元數大於，則`pbuffer`長度 為 ，運行時將返回ERROR_INSUFFICIENT_BUFFER。</span><span class="sxs-lookup"><span data-stu-id="96a55-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96a55-114">需求</span><span class="sxs-lookup"><span data-stu-id="96a55-114">Requirements</span></span>  
 <span data-ttu-id="96a55-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="96a55-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96a55-116">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="96a55-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96a55-117">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96a55-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96a55-118">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96a55-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96a55-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96a55-119">See also</span></span>

- [<span data-ttu-id="96a55-120">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="96a55-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
