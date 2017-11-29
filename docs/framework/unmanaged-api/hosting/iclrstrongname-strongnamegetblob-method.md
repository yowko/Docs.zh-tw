---
title: "ICLRStrongName::StrongNameGetBlob 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d4ae90367cb84c97d5964ceb815943249af7b240
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="d54fe-102">ICLRStrongName::StrongNameGetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="d54fe-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="d54fe-103">在指定位址之可執行檔的二進位表示法中填入指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d54fe-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d54fe-104">語法</span><span class="sxs-lookup"><span data-stu-id="d54fe-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d54fe-105">參數</span><span class="sxs-lookup"><span data-stu-id="d54fe-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d54fe-106">[in]要載入可執行檔的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="d54fe-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="d54fe-107">[in]在其中載入可執行檔的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d54fe-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="d54fe-108">[in、 out]要求的大小上限，以位元組為單位， `pbBlob`。</span><span class="sxs-lookup"><span data-stu-id="d54fe-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="d54fe-109">傳回時，實際的大小，以位元組為單位的`pbBlob`。</span><span class="sxs-lookup"><span data-stu-id="d54fe-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d54fe-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="d54fe-110">Return Value</span></span>  
 <span data-ttu-id="d54fe-111">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="d54fe-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d54fe-112">需求</span><span class="sxs-lookup"><span data-stu-id="d54fe-112">Requirements</span></span>  
 <span data-ttu-id="d54fe-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d54fe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d54fe-114">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d54fe-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d54fe-115">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d54fe-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d54fe-116">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d54fe-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d54fe-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d54fe-117">See Also</span></span>  
 [<span data-ttu-id="d54fe-118">StrongNameGetBlobFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="d54fe-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="d54fe-119">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="d54fe-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
