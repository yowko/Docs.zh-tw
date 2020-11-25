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
ms.openlocfilehash: 9590d19f4e5f5890af53a108492bd1b6d130fb72
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704496"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="a01b1-102">GetCORRequiredVersion 函式</span><span class="sxs-lookup"><span data-stu-id="a01b1-102">GetCORRequiredVersion Function</span></span>

<span data-ttu-id="a01b1-103">取得所需的 common language runtime (CLR) 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a01b1-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="a01b1-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="a01b1-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a01b1-105">語法</span><span class="sxs-lookup"><span data-stu-id="a01b1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a01b1-106">參數</span><span class="sxs-lookup"><span data-stu-id="a01b1-106">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="a01b1-107">擴展包含指定版本號碼之字串的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a01b1-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a01b1-108">在緩衝區的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="a01b1-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="a01b1-109">擴展緩衝區中傳回的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a01b1-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a01b1-110">需求</span><span class="sxs-lookup"><span data-stu-id="a01b1-110">Requirements</span></span>  

 <span data-ttu-id="a01b1-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a01b1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a01b1-112">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a01b1-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a01b1-113">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a01b1-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a01b1-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a01b1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a01b1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a01b1-115">See also</span></span>

- [<span data-ttu-id="a01b1-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="a01b1-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
