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
ms.openlocfilehash: f43a4e65442ca79ece71ce7e5e014309a611d7cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671600"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="24ec7-102">ICLRStrongName::StrongNameSignatureSize 方法</span><span class="sxs-lookup"><span data-stu-id="24ec7-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>

<span data-ttu-id="24ec7-103">傳回強式名稱簽章的大小。</span><span class="sxs-lookup"><span data-stu-id="24ec7-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="24ec7-104">編譯器通常會使用這個方法來判斷建立延遲簽署的元件時，檔案中要保留多少空間。</span><span class="sxs-lookup"><span data-stu-id="24ec7-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24ec7-105">語法</span><span class="sxs-lookup"><span data-stu-id="24ec7-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="24ec7-106">參數</span><span class="sxs-lookup"><span data-stu-id="24ec7-106">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="24ec7-107">在 [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) 類型的結構，其中包含用來產生強式名稱簽章之金鑰組的公開部分。</span><span class="sxs-lookup"><span data-stu-id="24ec7-107">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="24ec7-108">在的大小（以位元組為單位） `pbPublicKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="24ec7-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="24ec7-109">在儲存強式名稱簽章所需的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="24ec7-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24ec7-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="24ec7-110">Return Value</span></span>  

 <span data-ttu-id="24ec7-111">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="24ec7-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24ec7-112">需求</span><span class="sxs-lookup"><span data-stu-id="24ec7-112">Requirements</span></span>  

 <span data-ttu-id="24ec7-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24ec7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24ec7-114">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="24ec7-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="24ec7-115">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="24ec7-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24ec7-116">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24ec7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ec7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24ec7-117">See also</span></span>

- [<span data-ttu-id="24ec7-118">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="24ec7-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
