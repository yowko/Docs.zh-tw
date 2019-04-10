---
title: RunDll32ShimW 函式
ms.date: 03/30/2017
api_name:
- RunDll32ShimW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- RunDll32ShimW
helpviewer_keywords:
- RunDll32ShimW function [.NET Framework hosting]
ms.assetid: 9ea07b57-96e2-44df-8711-8fe6c119087f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccfdf9ffab35f076b85c067c2b412020a5f541b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231080"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="9a7e6-102">RunDll32ShimW 函式</span><span class="sxs-lookup"><span data-stu-id="9a7e6-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="9a7e6-103">執行指定命令。</span><span class="sxs-lookup"><span data-stu-id="9a7e6-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="9a7e6-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9a7e6-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a7e6-105">語法</span><span class="sxs-lookup"><span data-stu-id="9a7e6-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a7e6-106">參數</span><span class="sxs-lookup"><span data-stu-id="9a7e6-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="9a7e6-107">[in]將在其中顯示命令輸出的視窗控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9a7e6-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="9a7e6-108">[in]包含命令的文件庫控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9a7e6-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="9a7e6-109">[in]字串，指定要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="9a7e6-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="9a7e6-110">[in]整數，指定 [輸出] 視窗的顯示模式。</span><span class="sxs-lookup"><span data-stu-id="9a7e6-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a7e6-111">需求</span><span class="sxs-lookup"><span data-stu-id="9a7e6-111">Requirements</span></span>  
 <span data-ttu-id="9a7e6-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9a7e6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a7e6-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a7e6-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a7e6-114">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a7e6-114">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9a7e6-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="9a7e6-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9a7e6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a7e6-116">See also</span></span>

- [<span data-ttu-id="9a7e6-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="9a7e6-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
