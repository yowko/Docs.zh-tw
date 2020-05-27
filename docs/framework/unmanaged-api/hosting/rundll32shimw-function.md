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
ms.openlocfilehash: 90304eb94e6f53d3132c97f5ababdc45f6053d7c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006567"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="8f5f2-102">RunDll32ShimW 函式</span><span class="sxs-lookup"><span data-stu-id="8f5f2-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="8f5f2-103">執行指定命令。</span><span class="sxs-lookup"><span data-stu-id="8f5f2-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="8f5f2-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="8f5f2-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f5f2-105">語法</span><span class="sxs-lookup"><span data-stu-id="8f5f2-105">Syntax</span></span>  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f5f2-106">參數</span><span class="sxs-lookup"><span data-stu-id="8f5f2-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="8f5f2-107">在將顯示命令輸出之視窗的控制碼。</span><span class="sxs-lookup"><span data-stu-id="8f5f2-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="8f5f2-108">在包含命令之程式庫的控制碼。</span><span class="sxs-lookup"><span data-stu-id="8f5f2-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="8f5f2-109">在字串，指定要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="8f5f2-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="8f5f2-110">在整數，指定輸出視窗的顯示模式。</span><span class="sxs-lookup"><span data-stu-id="8f5f2-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f5f2-111">需求</span><span class="sxs-lookup"><span data-stu-id="8f5f2-111">Requirements</span></span>  
 <span data-ttu-id="8f5f2-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f5f2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f5f2-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="8f5f2-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f5f2-114">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="8f5f2-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f5f2-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f5f2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f5f2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f5f2-116">See also</span></span>

- [<span data-ttu-id="8f5f2-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="8f5f2-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
