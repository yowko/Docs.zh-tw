---
title: ICLRStrongName::GetHashFromHandle 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20c5f6bbb58b85f42ec00e356eccc5fb41ce813c
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339028"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="975b8-102">ICLRStrongName::GetHashFromHandle 方法</span><span class="sxs-lookup"><span data-stu-id="975b8-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="975b8-103">具有指定的檔案控制代碼，使用指定的雜湊演算法的檔案的內容中產生之雜湊。</span><span class="sxs-lookup"><span data-stu-id="975b8-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="975b8-104">語法</span><span class="sxs-lookup"><span data-stu-id="975b8-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="975b8-105">參數</span><span class="sxs-lookup"><span data-stu-id="975b8-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="975b8-106">[in]要雜湊的檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="975b8-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="975b8-107">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="975b8-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="975b8-108">使用零的預設演算法。</span><span class="sxs-lookup"><span data-stu-id="975b8-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="975b8-109">[out]傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="975b8-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="975b8-110">[in]要求的最大大小的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="975b8-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="975b8-111">[out]大小，以位元組為單位傳回`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="975b8-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="975b8-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="975b8-112">Return Value</span></span>  
 <span data-ttu-id="975b8-113">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="975b8-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="975b8-114">需求</span><span class="sxs-lookup"><span data-stu-id="975b8-114">Requirements</span></span>  
 <span data-ttu-id="975b8-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="975b8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="975b8-116">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="975b8-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="975b8-117">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="975b8-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="975b8-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="975b8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="975b8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="975b8-119">See Also</span></span>  
 [<span data-ttu-id="975b8-120">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="975b8-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
