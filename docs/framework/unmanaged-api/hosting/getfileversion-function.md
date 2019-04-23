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
ms.openlocfilehash: d25a3ccdd66ff7acb70f1f5e6c60157b53cc97c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123720"
---
# <a name="getfileversion-function"></a><span data-ttu-id="5c795-102">GetFileVersion 函式</span><span class="sxs-lookup"><span data-stu-id="5c795-102">GetFileVersion Function</span></span>
<span data-ttu-id="5c795-103">取得指定的檔案，並使用指定的緩衝區 common language runtime (CLR) 版本資訊。</span><span class="sxs-lookup"><span data-stu-id="5c795-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="5c795-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5c795-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c795-105">語法</span><span class="sxs-lookup"><span data-stu-id="5c795-105">Syntax</span></span>  
  
```  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c795-106">參數</span><span class="sxs-lookup"><span data-stu-id="5c795-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="5c795-107">[in]要檢查之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="5c795-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="5c795-108">[in、 out]傳回的版本資訊所配置的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5c795-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="5c795-109">[in]大小，以寬字元為單位的`szBuffer`。</span><span class="sxs-lookup"><span data-stu-id="5c795-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="5c795-110">[out]大小，以位元組為單位傳回`szBuffer`。</span><span class="sxs-lookup"><span data-stu-id="5c795-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c795-111">需求</span><span class="sxs-lookup"><span data-stu-id="5c795-111">Requirements</span></span>  
 <span data-ttu-id="5c795-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c795-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c795-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c795-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c795-114">**.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c795-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c795-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c795-115">See also</span></span>

- [<span data-ttu-id="5c795-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="5c795-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
