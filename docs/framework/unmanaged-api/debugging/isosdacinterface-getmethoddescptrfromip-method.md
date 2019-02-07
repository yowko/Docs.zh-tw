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
ms.openlocfilehash: 74853733b1fb7f023d9f192d3e862dbf6875ecda
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828596"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="2b4c8-102">ISOSDacInterface::GetMethodDescPtrFromIP 方法</span><span class="sxs-lookup"><span data-stu-id="2b4c8-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="2b4c8-103">擷取 MethodDesc 對應包含指定的原生指令位址之方法的指標。</span><span class="sxs-lookup"><span data-stu-id="2b4c8-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2b4c8-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b4c8-104">Syntax</span></span>

```
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

### <a name="parameters"></a><span data-ttu-id="2b4c8-105">參數</span><span class="sxs-lookup"><span data-stu-id="2b4c8-105">Parameters</span></span>

<span data-ttu-id="2b4c8-106">`ip` [in]在執行階段方法內的位址。</span><span class="sxs-lookup"><span data-stu-id="2b4c8-106">`ip` [in] An address within the method at runtime.</span></span>

<span data-ttu-id="2b4c8-107">`ppMD` [out]位址`MethodDesc`特定的方法。</span><span class="sxs-lookup"><span data-stu-id="2b4c8-107">`ppMD` [out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b4c8-108">備註</span><span class="sxs-lookup"><span data-stu-id="2b4c8-108">Remarks</span></span>

<span data-ttu-id="2b4c8-109">提供的方法是一部分[`ISOSDacInterface`介面](isosdacinterface-interface.md)，而對應的虛擬方法表 21 的位置。</span><span class="sxs-lookup"><span data-stu-id="2b4c8-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 21st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b4c8-110">需求</span><span class="sxs-lookup"><span data-stu-id="2b4c8-110">Requirements</span></span>

<span data-ttu-id="2b4c8-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2b4c8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2b4c8-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="2b4c8-112">**Header:** None</span></span>  
<span data-ttu-id="2b4c8-113">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="2b4c8-113">**Library:** None</span></span>  
<span data-ttu-id="2b4c8-114">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2b4c8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2b4c8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b4c8-115">See also</span></span>

- [<span data-ttu-id="2b4c8-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="2b4c8-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="2b4c8-117">ISOSDacInterface 介面</span><span class="sxs-lookup"><span data-stu-id="2b4c8-117">ISOSDacInterface Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
