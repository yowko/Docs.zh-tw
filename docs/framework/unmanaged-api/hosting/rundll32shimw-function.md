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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765163"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="e9198-102">RunDll32ShimW 函式</span><span class="sxs-lookup"><span data-stu-id="e9198-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="e9198-103">執行指定命令。</span><span class="sxs-lookup"><span data-stu-id="e9198-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="e9198-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e9198-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9198-105">語法</span><span class="sxs-lookup"><span data-stu-id="e9198-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9198-106">參數</span><span class="sxs-lookup"><span data-stu-id="e9198-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="e9198-107">[in]將在其中顯示命令輸出的視窗控制代碼。</span><span class="sxs-lookup"><span data-stu-id="e9198-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="e9198-108">[in]包含命令的文件庫控制代碼。</span><span class="sxs-lookup"><span data-stu-id="e9198-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="e9198-109">[in]字串，指定要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="e9198-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="e9198-110">[in]整數，指定 [輸出] 視窗的顯示模式。</span><span class="sxs-lookup"><span data-stu-id="e9198-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9198-111">需求</span><span class="sxs-lookup"><span data-stu-id="e9198-111">Requirements</span></span>  
 <span data-ttu-id="e9198-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9198-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9198-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9198-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9198-114">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e9198-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9198-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9198-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9198-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9198-116">See also</span></span>

- [<span data-ttu-id="e9198-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="e9198-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
