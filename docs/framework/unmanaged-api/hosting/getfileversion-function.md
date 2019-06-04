---
title: GetFileVersion 函式
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf63b2641c4140b287a3932c2073b445211ad3aa
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490363"
---
# <a name="getfileversion-function"></a><span data-ttu-id="bb581-102">GetFileVersion 函式</span><span class="sxs-lookup"><span data-stu-id="bb581-102">GetFileVersion Function</span></span>
<span data-ttu-id="bb581-103">取得指定的檔案，並使用指定的緩衝區 common language runtime (CLR) 版本資訊。</span><span class="sxs-lookup"><span data-stu-id="bb581-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="bb581-104">此函式已被取代，在.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="bb581-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb581-105">語法</span><span class="sxs-lookup"><span data-stu-id="bb581-105">Syntax</span></span>  
  
```  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb581-106">參數</span><span class="sxs-lookup"><span data-stu-id="bb581-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="bb581-107">[in]要檢查之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="bb581-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="bb581-108">[in、 out]傳回的版本資訊所配置的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bb581-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="bb581-109">[in]大小，以寬字元為單位的`szBuffer`。</span><span class="sxs-lookup"><span data-stu-id="bb581-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="bb581-110">[out]大小，以位元組為單位傳回`szBuffer`。</span><span class="sxs-lookup"><span data-stu-id="bb581-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb581-111">需求</span><span class="sxs-lookup"><span data-stu-id="bb581-111">Requirements</span></span>  
 <span data-ttu-id="bb581-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb581-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb581-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb581-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb581-114">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb581-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb581-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb581-115">See also</span></span>

- [<span data-ttu-id="bb581-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="bb581-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
