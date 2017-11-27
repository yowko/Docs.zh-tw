---
title: "GetFileVersion 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetFileVersion
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetFileVersion
helpviewer_keywords: GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 654cda723db9910fb80d32bc08c393a44f04b586
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="getfileversion-function"></a><span data-ttu-id="5b0b9-102">GetFileVersion 函式</span><span class="sxs-lookup"><span data-stu-id="5b0b9-102">GetFileVersion Function</span></span>
<span data-ttu-id="5b0b9-103">取得指定的檔案，使用指定的緩衝區 common language runtime (CLR) 版本資訊。</span><span class="sxs-lookup"><span data-stu-id="5b0b9-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="5b0b9-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5b0b9-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b0b9-105">語法</span><span class="sxs-lookup"><span data-stu-id="5b0b9-105">Syntax</span></span>  
  
```  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b0b9-106">參數</span><span class="sxs-lookup"><span data-stu-id="5b0b9-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="5b0b9-107">[in]要檢查檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="5b0b9-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="5b0b9-108">[in、 out]傳回的版本資訊已配置的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5b0b9-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="5b0b9-109">[in]大小，以寬字元為單位的`szBuffer`。</span><span class="sxs-lookup"><span data-stu-id="5b0b9-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="5b0b9-110">[out]大小，以位元組為單位傳回`szBuffer`。</span><span class="sxs-lookup"><span data-stu-id="5b0b9-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b0b9-111">需求</span><span class="sxs-lookup"><span data-stu-id="5b0b9-111">Requirements</span></span>  
 <span data-ttu-id="5b0b9-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b0b9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b0b9-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5b0b9-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b0b9-114">**.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b0b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b0b9-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b0b9-115">See Also</span></span>  
 [<span data-ttu-id="5b0b9-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="5b0b9-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
