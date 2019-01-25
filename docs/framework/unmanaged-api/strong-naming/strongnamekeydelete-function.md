---
title: StrongNameKeyDelete 函式
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3eace88e5034c61b7608a6d777608cc2544b8564
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688476"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="8f578-102">StrongNameKeyDelete 函式</span><span class="sxs-lookup"><span data-stu-id="8f578-102">StrongNameKeyDelete Function</span></span>
<span data-ttu-id="8f578-103">刪除指定的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="8f578-103">Deletes the specified key container.</span></span>  
  
 <span data-ttu-id="8f578-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="8f578-104">This function has been deprecated.</span></span> <span data-ttu-id="8f578-105">使用[iclrstrongname:: Strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="8f578-105">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f578-106">語法</span><span class="sxs-lookup"><span data-stu-id="8f578-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f578-107">參數</span><span class="sxs-lookup"><span data-stu-id="8f578-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="8f578-108">[in]若要刪除的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="8f578-108">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f578-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8f578-109">Return Value</span></span>  
 <span data-ttu-id="8f578-110">`true` 如果成功地完成;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="8f578-110">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f578-111">備註</span><span class="sxs-lookup"><span data-stu-id="8f578-111">Remarks</span></span>  
 <span data-ttu-id="8f578-112">使用[StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)函式以 importa 公開/私密金鑰組的容器。</span><span class="sxs-lookup"><span data-stu-id="8f578-112">Use the [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) function to importa a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="8f578-113">如果`StrongNameKeyDelete`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8f578-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f578-114">需求</span><span class="sxs-lookup"><span data-stu-id="8f578-114">Requirements</span></span>  
 <span data-ttu-id="8f578-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f578-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f578-116">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="8f578-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8f578-117">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8f578-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8f578-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f578-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f578-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f578-119">See also</span></span>
- [<span data-ttu-id="8f578-120">StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="8f578-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="8f578-121">StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="8f578-121">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="8f578-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="8f578-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
