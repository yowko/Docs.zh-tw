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
ms.openlocfilehash: 17d35193f69966e02ac5e483924fcb3ee2e06758
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799027"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="4bca4-102">StrongNameKeyDelete 函式</span><span class="sxs-lookup"><span data-stu-id="4bca4-102">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="4bca4-103">刪除指定的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="4bca4-103">Deletes the specified key container.</span></span>

<span data-ttu-id="4bca4-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="4bca4-104">This function has been deprecated.</span></span> <span data-ttu-id="4bca4-105">請改用[ICLRStrongName：： StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4bca4-105">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="4bca4-106">語法</span><span class="sxs-lookup"><span data-stu-id="4bca4-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="4bca4-107">參數</span><span class="sxs-lookup"><span data-stu-id="4bca4-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="4bca4-108">在要刪除的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="4bca4-108">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="4bca4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="4bca4-109">Return Value</span></span>

<span data-ttu-id="4bca4-110">`true`成功完成時;否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="4bca4-110">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4bca4-111">備註</span><span class="sxs-lookup"><span data-stu-id="4bca4-111">Remarks</span></span>

<span data-ttu-id="4bca4-112">使用[StrongNameKeyInstall](strongnamekeyinstall-function.md)函數，將公開/私密金鑰組匯入容器。</span><span class="sxs-lookup"><span data-stu-id="4bca4-112">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="4bca4-113">如果 `StrongNameKeyDelete` 函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4bca4-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="4bca4-114">需求</span><span class="sxs-lookup"><span data-stu-id="4bca4-114">Requirements</span></span>

<span data-ttu-id="4bca4-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4bca4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="4bca4-116">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="4bca4-116">**Header:** StrongName.h</span></span>

<span data-ttu-id="4bca4-117">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4bca4-117">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="4bca4-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bca4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4bca4-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bca4-119">See also</span></span>

- [<span data-ttu-id="4bca4-120">StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="4bca4-120">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="4bca4-121">StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="4bca4-121">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="4bca4-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="4bca4-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
