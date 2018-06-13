---
title: StrongNameKeyInstall 函式
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b6760a6418533f5c8f6cec815d86b4cff68aab1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460076"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="d31ab-102">StrongNameKeyInstall 函式</span><span class="sxs-lookup"><span data-stu-id="d31ab-102">StrongNameKeyInstall Function</span></span>
<span data-ttu-id="d31ab-103">匯入容器的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="d31ab-103">Imports a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="d31ab-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="d31ab-104">This function has been deprecated.</span></span> <span data-ttu-id="d31ab-105">使用[iclrstrongname:: Strongnamekeyinstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="d31ab-105">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d31ab-106">語法</span><span class="sxs-lookup"><span data-stu-id="d31ab-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d31ab-107">參數</span><span class="sxs-lookup"><span data-stu-id="d31ab-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="d31ab-108">[in]金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="d31ab-108">[in] The name of the key container.</span></span> <span data-ttu-id="d31ab-109">`wszKeyContainer` 必須是非空白字串。</span><span class="sxs-lookup"><span data-stu-id="d31ab-109">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="d31ab-110">[in]二進位的金鑰組。</span><span class="sxs-lookup"><span data-stu-id="d31ab-110">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="d31ab-111">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="d31ab-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d31ab-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="d31ab-112">Return Value</span></span>  
 <span data-ttu-id="d31ab-113">`true` 如果成功地完成。否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="d31ab-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d31ab-114">備註</span><span class="sxs-lookup"><span data-stu-id="d31ab-114">Remarks</span></span>  
 <span data-ttu-id="d31ab-115">使用[StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)函式來刪除金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="d31ab-115">Use the [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) function to delete the key container.</span></span>  
  
 <span data-ttu-id="d31ab-116">如果`StrongNameKeyInstall`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式可擷取的最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d31ab-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d31ab-117">需求</span><span class="sxs-lookup"><span data-stu-id="d31ab-117">Requirements</span></span>  
 <span data-ttu-id="d31ab-118">**平台：** WindSee[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d31ab-118">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d31ab-119">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d31ab-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d31ab-120">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d31ab-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d31ab-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d31ab-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d31ab-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d31ab-122">See Also</span></span>  
 [<span data-ttu-id="d31ab-123">StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="d31ab-123">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="d31ab-124">StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="d31ab-124">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="d31ab-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="d31ab-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
