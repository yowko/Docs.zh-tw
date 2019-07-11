---
title: ICLRStrongName::StrongNameGetBlob 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbc0262062eddb363b0a00535a2d099100124b67
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748073"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="0c0cc-102">ICLRStrongName::StrongNameGetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="0c0cc-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="0c0cc-103">使用位於所指定位址之可執行檔的二進位表示法填滿指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0c0cc-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c0cc-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c0cc-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c0cc-105">參數</span><span class="sxs-lookup"><span data-stu-id="0c0cc-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="0c0cc-106">[in]可執行檔載入有效的路徑。</span><span class="sxs-lookup"><span data-stu-id="0c0cc-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="0c0cc-107">[in]在其中載入可執行檔的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0c0cc-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="0c0cc-108">[in、 out]所要求大小上限，以位元組為單位， `pbBlob`。</span><span class="sxs-lookup"><span data-stu-id="0c0cc-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="0c0cc-109">傳回時，實際的大小，以位元組為單位的`pbBlob`。</span><span class="sxs-lookup"><span data-stu-id="0c0cc-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c0cc-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="0c0cc-110">Return Value</span></span>  
 <span data-ttu-id="0c0cc-111">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="0c0cc-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c0cc-112">需求</span><span class="sxs-lookup"><span data-stu-id="0c0cc-112">Requirements</span></span>  
 <span data-ttu-id="0c0cc-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c0cc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c0cc-114">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0c0cc-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0c0cc-115">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0c0cc-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c0cc-116">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c0cc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c0cc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c0cc-117">See also</span></span>

- [<span data-ttu-id="0c0cc-118">StrongNameGetBlobFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="0c0cc-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="0c0cc-119">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="0c0cc-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
