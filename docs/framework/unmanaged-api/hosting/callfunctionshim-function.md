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
ms.openlocfilehash: f72c987294d7768eacf112c622ab15494fb75e34
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685782"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="f2512-102">CallFunctionShim 函式</span><span class="sxs-lookup"><span data-stu-id="f2512-102">CallFunctionShim Function</span></span>

<span data-ttu-id="f2512-103">呼叫函式，該函式在指定的程式庫中具有指定的名稱和參數。</span><span class="sxs-lookup"><span data-stu-id="f2512-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="f2512-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="f2512-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2512-105">語法</span><span class="sxs-lookup"><span data-stu-id="f2512-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f2512-106">參數</span><span class="sxs-lookup"><span data-stu-id="f2512-106">Parameters</span></span>  

 `szDllName`  
 <span data-ttu-id="f2512-107">在包含函數的程式庫名稱。</span><span class="sxs-lookup"><span data-stu-id="f2512-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="f2512-108">在函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="f2512-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="f2512-109">在要傳遞至函數的第一個引數。</span><span class="sxs-lookup"><span data-stu-id="f2512-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="f2512-110">在要傳遞至函式的第二個引數。</span><span class="sxs-lookup"><span data-stu-id="f2512-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="f2512-111">在包含函數的程式庫版本。</span><span class="sxs-lookup"><span data-stu-id="f2512-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f2512-112">在保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="f2512-112">[in] Reserved for future use.</span></span> <span data-ttu-id="f2512-113">在此參數中傳遞零。</span><span class="sxs-lookup"><span data-stu-id="f2512-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2512-114">需求</span><span class="sxs-lookup"><span data-stu-id="f2512-114">Requirements</span></span>  

 <span data-ttu-id="f2512-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2512-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2512-116">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f2512-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2512-117">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2512-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2512-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2512-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2512-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2512-119">See also</span></span>

- [<span data-ttu-id="f2512-120">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="f2512-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
