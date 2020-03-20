---
title: ICLRStrongName::StrongNameSignatureSize 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: e789996af3aedd17251fc52cde52a336f65053ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176340"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="1bb23-102">ICLRStrongName::StrongNameSignatureSize 方法</span><span class="sxs-lookup"><span data-stu-id="1bb23-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="1bb23-103">傳回強式名稱簽章的大小。</span><span class="sxs-lookup"><span data-stu-id="1bb23-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="1bb23-104">編譯器通常使用此方法來確定在創建延遲簽名程式集時要在檔中保留多少空間。</span><span class="sxs-lookup"><span data-stu-id="1bb23-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bb23-105">語法</span><span class="sxs-lookup"><span data-stu-id="1bb23-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="1bb23-106">參數</span><span class="sxs-lookup"><span data-stu-id="1bb23-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="1bb23-107">[在][公共金鑰Blob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)類型的結構，其中包含用於生成強式名稱簽名的金鑰組的公共部分。</span><span class="sxs-lookup"><span data-stu-id="1bb23-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="1bb23-108">[在]的大小（以位元組為單位）的大小`pbPublicKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="1bb23-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="1bb23-109">[在]存儲強式名稱簽名所需的位元組數。</span><span class="sxs-lookup"><span data-stu-id="1bb23-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bb23-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="1bb23-110">Return Value</span></span>  
 <span data-ttu-id="1bb23-111">`S_OK`如果方法成功完成;如果方法成功完成;否則，指示失敗的 HRESULT 值（請參閱清單[的常用 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="1bb23-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bb23-112">需求</span><span class="sxs-lookup"><span data-stu-id="1bb23-112">Requirements</span></span>  
 <span data-ttu-id="1bb23-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1bb23-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bb23-114">**標題：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1bb23-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1bb23-115">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1bb23-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1bb23-116">**.NET 框架版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bb23-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bb23-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bb23-117">See also</span></span>

- [<span data-ttu-id="1bb23-118">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="1bb23-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
