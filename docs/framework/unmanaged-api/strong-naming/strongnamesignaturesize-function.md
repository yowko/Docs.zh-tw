---
title: StrongNameSignatureSize 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: a19d875b8fb81f2af3821e69452f0f0ed591cd22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176886"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="ec367-102">StrongNameSignatureSize 函式</span><span class="sxs-lookup"><span data-stu-id="ec367-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="ec367-103">傳回強式名稱簽章的大小。</span><span class="sxs-lookup"><span data-stu-id="ec367-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="ec367-104">`StrongNameSignatureSize`編譯器通常用於確定在創建延遲簽名程式集時檔中保留的空間。</span><span class="sxs-lookup"><span data-stu-id="ec367-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="ec367-105">此函數已被棄用。</span><span class="sxs-lookup"><span data-stu-id="ec367-105">This function has been deprecated.</span></span> <span data-ttu-id="ec367-106">改用[ICLR 強式名稱：：強式名稱簽名大小](../hosting/iclrstrongname-strongnamesignaturesize-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ec367-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec367-107">語法</span><span class="sxs-lookup"><span data-stu-id="ec367-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="ec367-108">參數</span><span class="sxs-lookup"><span data-stu-id="ec367-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="ec367-109">[在][公共金鑰Blob](publickeyblob-structure.md)類型的結構，其中包含用於生成強式名稱簽名的金鑰組的公共部分。</span><span class="sxs-lookup"><span data-stu-id="ec367-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="ec367-110">[在]的大小（以位元組為單位）的大小`pbPublicKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="ec367-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="ec367-111">[在]存儲強式名稱簽名所需的位元組數。</span><span class="sxs-lookup"><span data-stu-id="ec367-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec367-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="ec367-112">Return Value</span></span>  
 <span data-ttu-id="ec367-113">`true`成功完成;否則， `false`.</span><span class="sxs-lookup"><span data-stu-id="ec367-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec367-114">備註</span><span class="sxs-lookup"><span data-stu-id="ec367-114">Remarks</span></span>  
 <span data-ttu-id="ec367-115">如果`StrongNameSignatureSize`函數未成功完成，請調用[StrongNameErrorInfo 函數](strongnameerrorinfo-function.md)以檢索上次生成的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ec367-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec367-116">需求</span><span class="sxs-lookup"><span data-stu-id="ec367-116">Requirements</span></span>  
 <span data-ttu-id="ec367-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec367-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec367-118">**標題：** 強式名稱.h</span><span class="sxs-lookup"><span data-stu-id="ec367-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ec367-119">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ec367-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec367-120">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec367-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec367-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec367-121">See also</span></span>

- [<span data-ttu-id="ec367-122">StrongNameSignatureSize 方法</span><span class="sxs-lookup"><span data-stu-id="ec367-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="ec367-123">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="ec367-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
