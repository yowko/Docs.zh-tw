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
ms.openlocfilehash: 6b9fd62102056a8d5f859ac913f4786f04c1df7e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617239"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="c1ff8-102">GetCORRequiredVersion 函式</span><span class="sxs-lookup"><span data-stu-id="c1ff8-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="c1ff8-103">取得所需的 common language runtime （CLR）版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c1ff8-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="c1ff8-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="c1ff8-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ff8-105">語法</span><span class="sxs-lookup"><span data-stu-id="c1ff8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1ff8-106">參數</span><span class="sxs-lookup"><span data-stu-id="c1ff8-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="c1ff8-107">脫銷包含指定版本號碼之字串的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c1ff8-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="c1ff8-108">在緩衝區的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="c1ff8-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="c1ff8-109">脫銷緩衝區中傳回的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="c1ff8-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1ff8-110">需求</span><span class="sxs-lookup"><span data-stu-id="c1ff8-110">Requirements</span></span>  
 <span data-ttu-id="c1ff8-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c1ff8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1ff8-112">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="c1ff8-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1ff8-113">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="c1ff8-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1ff8-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1ff8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ff8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1ff8-115">See also</span></span>

- [<span data-ttu-id="c1ff8-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="c1ff8-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
