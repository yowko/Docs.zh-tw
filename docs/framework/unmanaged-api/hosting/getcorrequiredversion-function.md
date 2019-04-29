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
ms.openlocfilehash: b5786444c36fcfc9547be1db0006757b0a9376c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628092"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="b3569-102">GetCORRequiredVersion 函式</span><span class="sxs-lookup"><span data-stu-id="b3569-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="b3569-103">取得必要 common language runtime (CLR) 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b3569-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="b3569-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b3569-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3569-105">語法</span><span class="sxs-lookup"><span data-stu-id="b3569-105">Syntax</span></span>  
  
```  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3569-106">參數</span><span class="sxs-lookup"><span data-stu-id="b3569-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="b3569-107">[out]緩衝區，包含指定的版本號碼的字串。</span><span class="sxs-lookup"><span data-stu-id="b3569-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="b3569-108">[in]以位元組為單位的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="b3569-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="b3569-109">[out]傳回緩衝區中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="b3569-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3569-110">需求</span><span class="sxs-lookup"><span data-stu-id="b3569-110">Requirements</span></span>  
 <span data-ttu-id="b3569-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3569-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3569-112">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b3569-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3569-113">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3569-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3569-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3569-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3569-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3569-115">See also</span></span>

- [<span data-ttu-id="b3569-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="b3569-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
