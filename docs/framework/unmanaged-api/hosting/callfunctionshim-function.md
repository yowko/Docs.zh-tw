---
title: "CallFunctionShim 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CallFunctionShim
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CallFunctionShim
helpviewer_keywords: CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e6e2e237887ff273ba73e2568c84d2aaaa38383
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="10df9-102">CallFunctionShim 函式</span><span class="sxs-lookup"><span data-stu-id="10df9-102">CallFunctionShim Function</span></span>
<span data-ttu-id="10df9-103">會指定程式庫中有指定的名稱和參數的函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="10df9-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="10df9-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="10df9-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10df9-105">語法</span><span class="sxs-lookup"><span data-stu-id="10df9-105">Syntax</span></span>  
  
```  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10df9-106">參數</span><span class="sxs-lookup"><span data-stu-id="10df9-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="10df9-107">[in]包含函式的程式庫名稱。</span><span class="sxs-lookup"><span data-stu-id="10df9-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="10df9-108">[in]函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="10df9-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="10df9-109">[in]要傳遞給函式的第一個引數。</span><span class="sxs-lookup"><span data-stu-id="10df9-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="10df9-110">[in]第二個引數傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="10df9-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="10df9-111">[in]包含函式的程式庫版本。</span><span class="sxs-lookup"><span data-stu-id="10df9-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="10df9-112">[in]保留供未來使用。</span><span class="sxs-lookup"><span data-stu-id="10df9-112">[in] Reserved for future use.</span></span> <span data-ttu-id="10df9-113">傳遞此參數中的零。</span><span class="sxs-lookup"><span data-stu-id="10df9-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10df9-114">需求</span><span class="sxs-lookup"><span data-stu-id="10df9-114">Requirements</span></span>  
 <span data-ttu-id="10df9-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10df9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10df9-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="10df9-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10df9-117">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="10df9-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10df9-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10df9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10df9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10df9-119">See Also</span></span>  
 [<span data-ttu-id="10df9-120">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="10df9-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
