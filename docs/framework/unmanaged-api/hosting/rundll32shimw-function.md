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
ms.openlocfilehash: 18247a947449ea5fd19f1882031b598086332742
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441736"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="b9f36-102">RunDll32ShimW 函式</span><span class="sxs-lookup"><span data-stu-id="b9f36-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="b9f36-103">執行指定命令。</span><span class="sxs-lookup"><span data-stu-id="b9f36-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="b9f36-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b9f36-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9f36-105">語法</span><span class="sxs-lookup"><span data-stu-id="b9f36-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9f36-106">參數</span><span class="sxs-lookup"><span data-stu-id="b9f36-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="b9f36-107">[in]會顯示命令輸出的視窗控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b9f36-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="b9f36-108">[in]包含命令的文件庫的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b9f36-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="b9f36-109">[in]字串，指定要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="b9f36-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="b9f36-110">[in]整數，指定 [輸出] 視窗的顯示模式。</span><span class="sxs-lookup"><span data-stu-id="b9f36-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9f36-111">需求</span><span class="sxs-lookup"><span data-stu-id="b9f36-111">Requirements</span></span>  
 <span data-ttu-id="b9f36-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9f36-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9f36-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b9f36-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9f36-114">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b9f36-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9f36-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9f36-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f36-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9f36-116">See Also</span></span>  
 [<span data-ttu-id="b9f36-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="b9f36-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
