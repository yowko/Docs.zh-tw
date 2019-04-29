---
title: IXCLRDataMethodInstance::GetRepresentativeEntryAddress 方法
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 6f204e2ed9cb1409d53432355467bb11946f8809
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775527"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="ff787-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress 方法</span><span class="sxs-lookup"><span data-stu-id="ff787-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="ff787-103">取得所有可能的進入點之方法的原生編譯的最具代表性的進入點位址。</span><span class="sxs-lookup"><span data-stu-id="ff787-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ff787-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff787-104">Syntax</span></span>

```
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="ff787-105">參數</span><span class="sxs-lookup"><span data-stu-id="ff787-105">Parameters</span></span>

`addr`\
<span data-ttu-id="ff787-106">[out]最具代表性的原生進入點方法的位址。</span><span class="sxs-lookup"><span data-stu-id="ff787-106">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff787-107">備註</span><span class="sxs-lookup"><span data-stu-id="ff787-107">Remarks</span></span>

<span data-ttu-id="ff787-108">提供的方法是一部分[`IXCLRDataMethodInstance`介面](ixclrdatamethodinstance-interface.md)，而對應的虛擬方法表 19 位置。</span><span class="sxs-lookup"><span data-stu-id="ff787-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 19th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ff787-109">需求</span><span class="sxs-lookup"><span data-stu-id="ff787-109">Requirements</span></span>

<span data-ttu-id="ff787-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff787-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ff787-111">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="ff787-111">**Header:** None</span></span>  
<span data-ttu-id="ff787-112">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="ff787-112">**Library:** None</span></span>  
<span data-ttu-id="ff787-113">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ff787-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ff787-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff787-114">See also</span></span>

- [<span data-ttu-id="ff787-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="ff787-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="ff787-116">IXCLRDataMethodInstance 介面</span><span class="sxs-lookup"><span data-stu-id="ff787-116">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
