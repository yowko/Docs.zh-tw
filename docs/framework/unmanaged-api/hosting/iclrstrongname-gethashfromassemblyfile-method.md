---
title: "ICLRStrongName::GetHashFromAssemblyFile 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6dcb0ca16c2ffdd8a928cec9cca44b628de34885
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="93a7b-102">ICLRStrongName::GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="93a7b-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="93a7b-103">取得指定的組件檔案，使用指定的雜湊演算法的雜湊。</span><span class="sxs-lookup"><span data-stu-id="93a7b-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93a7b-104">語法</span><span class="sxs-lookup"><span data-stu-id="93a7b-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93a7b-105">參數</span><span class="sxs-lookup"><span data-stu-id="93a7b-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="93a7b-106">[in]要雜湊檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="93a7b-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="93a7b-107">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="93a7b-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="93a7b-108">使用預設雜湊演算法的零。</span><span class="sxs-lookup"><span data-stu-id="93a7b-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="93a7b-109">[out]傳回雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="93a7b-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="93a7b-110">[in]要求的大小上限的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="93a7b-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="93a7b-111">[out]傳回的大小，以位元組為單位， `pbHash`。</span><span class="sxs-lookup"><span data-stu-id="93a7b-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93a7b-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="93a7b-112">Return Value</span></span>  
 <span data-ttu-id="93a7b-113">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="93a7b-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93a7b-114">需求</span><span class="sxs-lookup"><span data-stu-id="93a7b-114">Requirements</span></span>  
 <span data-ttu-id="93a7b-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93a7b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93a7b-116">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="93a7b-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="93a7b-117">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="93a7b-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93a7b-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93a7b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a7b-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="93a7b-119">See Also</span></span>  
 [<span data-ttu-id="93a7b-120">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="93a7b-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="93a7b-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="93a7b-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
