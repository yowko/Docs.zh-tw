---
title: CallFunctionShim 函式
ms.date: 03/30/2017
api_name:
- CallFunctionShim
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CallFunctionShim
helpviewer_keywords:
- CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type:
- apiref
ms.openlocfilehash: d39e15a2ba71ba0c0147482259f5618dcb5d298b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192100"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="1d5bb-102">CallFunctionShim 函式</span><span class="sxs-lookup"><span data-stu-id="1d5bb-102">CallFunctionShim Function</span></span>
<span data-ttu-id="1d5bb-103">呼叫在指定的程式庫中具有指定名稱和參數的函式。</span><span class="sxs-lookup"><span data-stu-id="1d5bb-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="1d5bb-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="1d5bb-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d5bb-105">語法</span><span class="sxs-lookup"><span data-stu-id="1d5bb-105">Syntax</span></span>  
  
```cpp  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d5bb-106">參數</span><span class="sxs-lookup"><span data-stu-id="1d5bb-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="1d5bb-107">在包含函數之程式庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d5bb-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="1d5bb-108">在函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d5bb-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="1d5bb-109">在要傳遞至函式的第一個引數。</span><span class="sxs-lookup"><span data-stu-id="1d5bb-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="1d5bb-110">在要傳遞至函式的第二個引數。</span><span class="sxs-lookup"><span data-stu-id="1d5bb-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="1d5bb-111">在包含函數的程式庫版本。</span><span class="sxs-lookup"><span data-stu-id="1d5bb-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="1d5bb-112">在保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="1d5bb-112">[in] Reserved for future use.</span></span> <span data-ttu-id="1d5bb-113">在此參數中傳遞零。</span><span class="sxs-lookup"><span data-stu-id="1d5bb-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d5bb-114">需求</span><span class="sxs-lookup"><span data-stu-id="1d5bb-114">Requirements</span></span>  
 <span data-ttu-id="1d5bb-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d5bb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d5bb-116">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="1d5bb-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d5bb-117">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="1d5bb-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d5bb-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d5bb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d5bb-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="1d5bb-119">See also</span></span>

- [<span data-ttu-id="1d5bb-120">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="1d5bb-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
