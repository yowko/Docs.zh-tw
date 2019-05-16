---
title: ISOSDacInterface::GetMethodDescPtrFromIP 方法
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c92b112262aa2bede03bddc1396947b5fdfd6286
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629995"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="57da3-102">ISOSDacInterface::GetMethodDescPtrFromIP 方法</span><span class="sxs-lookup"><span data-stu-id="57da3-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="57da3-103">擷取 MethodDesc 對應包含指定的原生指令位址之方法的指標。</span><span class="sxs-lookup"><span data-stu-id="57da3-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="57da3-104">語法</span><span class="sxs-lookup"><span data-stu-id="57da3-104">Syntax</span></span>

```
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="57da3-105">參數</span><span class="sxs-lookup"><span data-stu-id="57da3-105">Parameters</span></span>

`ip`\
<span data-ttu-id="57da3-106">[in]在執行階段方法內的位址。</span><span class="sxs-lookup"><span data-stu-id="57da3-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="57da3-107">[out]位址`MethodDesc`特定的方法。</span><span class="sxs-lookup"><span data-stu-id="57da3-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="57da3-108">備註</span><span class="sxs-lookup"><span data-stu-id="57da3-108">Remarks</span></span>

<span data-ttu-id="57da3-109">提供的方法是一部分[`ISOSDacInterface`介面](isosdacinterface-interface.md)，而對應的虛擬方法表 21 的位置。</span><span class="sxs-lookup"><span data-stu-id="57da3-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 21st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="57da3-110">需求</span><span class="sxs-lookup"><span data-stu-id="57da3-110">Requirements</span></span>

<span data-ttu-id="57da3-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="57da3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="57da3-112">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="57da3-112">**Header:** None</span></span>  
<span data-ttu-id="57da3-113">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="57da3-113">**Library:** None</span></span>  
<span data-ttu-id="57da3-114">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="57da3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="57da3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57da3-115">See also</span></span>

- [<span data-ttu-id="57da3-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="57da3-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="57da3-117">ISOSDacInterface 介面</span><span class="sxs-lookup"><span data-stu-id="57da3-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
