---
title: "GetCORRequiredVersion 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORRequiredVersion
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetCORRequiredVersion
helpviewer_keywords: GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65505243d7d1691f0458d614fd878b054916f113
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="0ca7d-102">GetCORRequiredVersion 函式</span><span class="sxs-lookup"><span data-stu-id="0ca7d-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="0ca7d-103">取得必要 common language runtime (CLR) 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="0ca7d-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="0ca7d-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0ca7d-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ca7d-105">語法</span><span class="sxs-lookup"><span data-stu-id="0ca7d-105">Syntax</span></span>  
  
```  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ca7d-106">參數</span><span class="sxs-lookup"><span data-stu-id="0ca7d-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="0ca7d-107">[out]緩衝區，其中包含指定的版本號碼的字串。</span><span class="sxs-lookup"><span data-stu-id="0ca7d-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="0ca7d-108">[in]以位元組為單位的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="0ca7d-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="0ca7d-109">[out]傳回緩衝區中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0ca7d-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ca7d-110">需求</span><span class="sxs-lookup"><span data-stu-id="0ca7d-110">Requirements</span></span>  
 <span data-ttu-id="0ca7d-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ca7d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ca7d-112">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0ca7d-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ca7d-113">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ca7d-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ca7d-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ca7d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca7d-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ca7d-115">See Also</span></span>  
 [<span data-ttu-id="0ca7d-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="0ca7d-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
