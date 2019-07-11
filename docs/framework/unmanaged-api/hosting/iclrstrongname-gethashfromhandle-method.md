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
ms.openlocfilehash: a8f6878d714704370c3f43451c9995a7c5adb5d1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748143"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="2057f-102">ICLRStrongName::GetHashFromHandle 方法</span><span class="sxs-lookup"><span data-stu-id="2057f-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="2057f-103">具有指定的檔案控制代碼，使用指定的雜湊演算法的檔案的內容中產生之雜湊。</span><span class="sxs-lookup"><span data-stu-id="2057f-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2057f-104">語法</span><span class="sxs-lookup"><span data-stu-id="2057f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2057f-105">參數</span><span class="sxs-lookup"><span data-stu-id="2057f-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="2057f-106">[in]要雜湊的檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="2057f-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2057f-107">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="2057f-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="2057f-108">使用零的預設演算法。</span><span class="sxs-lookup"><span data-stu-id="2057f-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2057f-109">[out]傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2057f-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2057f-110">[in]要求的最大大小的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="2057f-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2057f-111">[out]大小，以位元組為單位傳回`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="2057f-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2057f-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="2057f-112">Return Value</span></span>  
 <span data-ttu-id="2057f-113">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="2057f-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2057f-114">需求</span><span class="sxs-lookup"><span data-stu-id="2057f-114">Requirements</span></span>  
 <span data-ttu-id="2057f-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2057f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2057f-116">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2057f-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2057f-117">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2057f-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2057f-118">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2057f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2057f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2057f-119">See also</span></span>

- [<span data-ttu-id="2057f-120">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="2057f-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
