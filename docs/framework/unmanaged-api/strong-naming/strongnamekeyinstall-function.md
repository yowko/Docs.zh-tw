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
ms.openlocfilehash: 9e441d4da64e9704fbda2368d2b07289aaea610a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125202"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="cb213-102">StrongNameKeyInstall 函式</span><span class="sxs-lookup"><span data-stu-id="cb213-102">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="cb213-103">將公開/私密金鑰組匯入到容器中。</span><span class="sxs-lookup"><span data-stu-id="cb213-103">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="cb213-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="cb213-104">This function has been deprecated.</span></span> <span data-ttu-id="cb213-105">請改用[ICLRStrongName：： StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="cb213-105">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="cb213-106">語法</span><span class="sxs-lookup"><span data-stu-id="cb213-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="cb213-107">參數</span><span class="sxs-lookup"><span data-stu-id="cb213-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="cb213-108">在金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="cb213-108">[in] The name of the key container.</span></span> <span data-ttu-id="cb213-109">`wszKeyContainer` 必須是非空白字串。</span><span class="sxs-lookup"><span data-stu-id="cb213-109">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="cb213-110">在二進位金鑰組。</span><span class="sxs-lookup"><span data-stu-id="cb213-110">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="cb213-111">在`pbKeyBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="cb213-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="cb213-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="cb213-112">Return Value</span></span>

<span data-ttu-id="cb213-113">成功完成時 `true`;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="cb213-113">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb213-114">備註</span><span class="sxs-lookup"><span data-stu-id="cb213-114">Remarks</span></span>

<span data-ttu-id="cb213-115">使用[StrongNameKeyDelete](strongnamekeydelete-function.md)函數來刪除金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="cb213-115">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="cb213-116">如果 `StrongNameKeyInstall` 函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="cb213-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb213-117">需求</span><span class="sxs-lookup"><span data-stu-id="cb213-117">Requirements</span></span>

<span data-ttu-id="cb213-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb213-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="cb213-119">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="cb213-119">**Header:** StrongName.h</span></span>

<span data-ttu-id="cb213-120">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cb213-120">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="cb213-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb213-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cb213-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="cb213-122">See also</span></span>

- [<span data-ttu-id="cb213-123">StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="cb213-123">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="cb213-124">StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="cb213-124">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="cb213-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="cb213-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
