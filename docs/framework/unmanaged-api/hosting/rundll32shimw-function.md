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
ms.openlocfilehash: dd053134792b80a006849e465bc0025cf77a9ad8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729950"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="2122b-102">RunDll32ShimW 函式</span><span class="sxs-lookup"><span data-stu-id="2122b-102">RunDll32ShimW Function</span></span>

<span data-ttu-id="2122b-103">執行指定命令。</span><span class="sxs-lookup"><span data-stu-id="2122b-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="2122b-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="2122b-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2122b-105">語法</span><span class="sxs-lookup"><span data-stu-id="2122b-105">Syntax</span></span>  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2122b-106">參數</span><span class="sxs-lookup"><span data-stu-id="2122b-106">Parameters</span></span>  

 `hwnd`  
 <span data-ttu-id="2122b-107">在視窗的控制碼，會在其中顯示命令輸出。</span><span class="sxs-lookup"><span data-stu-id="2122b-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="2122b-108">在包含命令的程式庫控制碼。</span><span class="sxs-lookup"><span data-stu-id="2122b-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="2122b-109">在字串，指定要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="2122b-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="2122b-110">在指定輸出視窗顯示模式的整數。</span><span class="sxs-lookup"><span data-stu-id="2122b-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2122b-111">需求</span><span class="sxs-lookup"><span data-stu-id="2122b-111">Requirements</span></span>  

 <span data-ttu-id="2122b-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2122b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2122b-113">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2122b-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2122b-114">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2122b-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2122b-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2122b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2122b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2122b-116">See also</span></span>

- [<span data-ttu-id="2122b-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="2122b-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
