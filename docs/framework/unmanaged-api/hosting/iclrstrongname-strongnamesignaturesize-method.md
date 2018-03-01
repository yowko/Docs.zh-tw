---
title: "ICLRStrongName::StrongNameSignatureSize 方法"
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
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a961cca6bba24ac8a2428a20c616a2ee074b8abf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="23f7c-102">ICLRStrongName::StrongNameSignatureSize 方法</span><span class="sxs-lookup"><span data-stu-id="23f7c-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="23f7c-103">傳回強式名稱簽章的大小。</span><span class="sxs-lookup"><span data-stu-id="23f7c-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="23f7c-104">這個方法通常是由編譯器決定要建立的延遲簽署組件時，檔案中保留多少空間。</span><span class="sxs-lookup"><span data-stu-id="23f7c-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23f7c-105">語法</span><span class="sxs-lookup"><span data-stu-id="23f7c-105">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="23f7c-106">參數</span><span class="sxs-lookup"><span data-stu-id="23f7c-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="23f7c-107">[in]型別的結構[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) ，其中包含用來產生強式名稱簽章金鑰組的公開部分。</span><span class="sxs-lookup"><span data-stu-id="23f7c-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="23f7c-108">[in]大小，以位元組為單位的`pbPublicKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="23f7c-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="23f7c-109">[in]儲存的強式名稱簽章所需的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="23f7c-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23f7c-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="23f7c-110">Return Value</span></span>  
 <span data-ttu-id="23f7c-111">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="23f7c-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23f7c-112">需求</span><span class="sxs-lookup"><span data-stu-id="23f7c-112">Requirements</span></span>  
 <span data-ttu-id="23f7c-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23f7c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23f7c-114">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="23f7c-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="23f7c-115">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="23f7c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23f7c-116">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23f7c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f7c-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="23f7c-117">See Also</span></span>  
 [<span data-ttu-id="23f7c-118">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="23f7c-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
