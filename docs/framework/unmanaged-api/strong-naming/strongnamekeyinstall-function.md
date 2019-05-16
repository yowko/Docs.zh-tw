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
ms.openlocfilehash: 7121ace6777e7cf947fcc6ff30b1ea314851feff
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636709"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="30fd1-102">StrongNameKeyInstall 函式</span><span class="sxs-lookup"><span data-stu-id="30fd1-102">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="30fd1-103">將公開/私密金鑰組匯入到容器中。</span><span class="sxs-lookup"><span data-stu-id="30fd1-103">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="30fd1-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="30fd1-104">This function has been deprecated.</span></span> <span data-ttu-id="30fd1-105">使用[iclrstrongname:: Strongnamekeyinstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="30fd1-105">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="30fd1-106">語法</span><span class="sxs-lookup"><span data-stu-id="30fd1-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="30fd1-107">參數</span><span class="sxs-lookup"><span data-stu-id="30fd1-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="30fd1-108">[in]金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="30fd1-108">[in] The name of the key container.</span></span> <span data-ttu-id="30fd1-109">`wszKeyContainer` 必須是非空白字串。</span><span class="sxs-lookup"><span data-stu-id="30fd1-109">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="30fd1-110">[in]二進位金鑰組。</span><span class="sxs-lookup"><span data-stu-id="30fd1-110">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="30fd1-111">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="30fd1-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="30fd1-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="30fd1-112">Return Value</span></span>

<span data-ttu-id="30fd1-113">`true` 如果成功地完成;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="30fd1-113">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="30fd1-114">備註</span><span class="sxs-lookup"><span data-stu-id="30fd1-114">Remarks</span></span>

<span data-ttu-id="30fd1-115">使用[StrongNameKeyDelete](strongnamekeydelete-function.md)函式來刪除金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="30fd1-115">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="30fd1-116">如果`StrongNameKeyInstall`函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="30fd1-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="30fd1-117">需求</span><span class="sxs-lookup"><span data-stu-id="30fd1-117">Requirements</span></span>

<span data-ttu-id="30fd1-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30fd1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="30fd1-119">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="30fd1-119">**Header:** StrongName.h</span></span>

<span data-ttu-id="30fd1-120">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="30fd1-120">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="30fd1-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30fd1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="30fd1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30fd1-122">See also</span></span>

- [<span data-ttu-id="30fd1-123">StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="30fd1-123">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="30fd1-124">StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="30fd1-124">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="30fd1-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="30fd1-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
