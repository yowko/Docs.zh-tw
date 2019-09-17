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
ms.openlocfilehash: 353898b72f41acd0c49a43ff05e54f61b99444c4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799001"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="70d1e-102">StrongNameKeyInstall 函式</span><span class="sxs-lookup"><span data-stu-id="70d1e-102">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="70d1e-103">將公開/私密金鑰組匯入到容器中。</span><span class="sxs-lookup"><span data-stu-id="70d1e-103">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="70d1e-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="70d1e-104">This function has been deprecated.</span></span> <span data-ttu-id="70d1e-105">請改用[ICLRStrongName：： StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="70d1e-105">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="70d1e-106">語法</span><span class="sxs-lookup"><span data-stu-id="70d1e-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="70d1e-107">參數</span><span class="sxs-lookup"><span data-stu-id="70d1e-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="70d1e-108">在金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="70d1e-108">[in] The name of the key container.</span></span> <span data-ttu-id="70d1e-109">`wszKeyContainer`必須是非空白字串。</span><span class="sxs-lookup"><span data-stu-id="70d1e-109">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="70d1e-110">在二進位金鑰組。</span><span class="sxs-lookup"><span data-stu-id="70d1e-110">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="70d1e-111">在的大小（以位元組為單位`pbKeyBlob`）。</span><span class="sxs-lookup"><span data-stu-id="70d1e-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="70d1e-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="70d1e-112">Return Value</span></span>

<span data-ttu-id="70d1e-113">`true`成功完成時;否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="70d1e-113">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="70d1e-114">備註</span><span class="sxs-lookup"><span data-stu-id="70d1e-114">Remarks</span></span>

<span data-ttu-id="70d1e-115">使用[StrongNameKeyDelete](strongnamekeydelete-function.md)函數來刪除金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="70d1e-115">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="70d1e-116">如果 `StrongNameKeyInstall`函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="70d1e-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="70d1e-117">需求</span><span class="sxs-lookup"><span data-stu-id="70d1e-117">Requirements</span></span>

<span data-ttu-id="70d1e-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70d1e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="70d1e-119">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="70d1e-119">**Header:** StrongName.h</span></span>

<span data-ttu-id="70d1e-120">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="70d1e-120">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="70d1e-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70d1e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="70d1e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70d1e-122">See also</span></span>

- [<span data-ttu-id="70d1e-123">StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="70d1e-123">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="70d1e-124">StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="70d1e-124">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="70d1e-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="70d1e-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
