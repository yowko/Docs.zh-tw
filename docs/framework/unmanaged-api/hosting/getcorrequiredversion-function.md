---
title: GetCORRequiredVersion 函式
ms.date: 03/30/2017
api_name:
- GetCORRequiredVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetCORRequiredVersion
helpviewer_keywords:
- GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 637ff0fca74dc123a3f7a47dcc3fdeded8d884ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430043"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="7e15f-102">GetCORRequiredVersion 函式</span><span class="sxs-lookup"><span data-stu-id="7e15f-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="7e15f-103">取得必要 common language runtime (CLR) 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="7e15f-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="7e15f-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7e15f-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e15f-105">語法</span><span class="sxs-lookup"><span data-stu-id="7e15f-105">Syntax</span></span>  
  
```  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e15f-106">參數</span><span class="sxs-lookup"><span data-stu-id="7e15f-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="7e15f-107">[out]緩衝區，其中包含指定的版本號碼的字串。</span><span class="sxs-lookup"><span data-stu-id="7e15f-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7e15f-108">[in]以位元組為單位的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="7e15f-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="7e15f-109">[out]傳回緩衝區中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="7e15f-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e15f-110">需求</span><span class="sxs-lookup"><span data-stu-id="7e15f-110">Requirements</span></span>  
 <span data-ttu-id="7e15f-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e15f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e15f-112">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7e15f-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e15f-113">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e15f-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e15f-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e15f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e15f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e15f-115">See Also</span></span>  
 [<span data-ttu-id="7e15f-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="7e15f-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
