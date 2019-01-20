---
title: IXCLRDataProcess::EnumMethodInstanceByAddress 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b42939e8e64e75337478ace67a9a91c6a03a94e3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416463"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="f1380-102">IXCLRDataProcess::EnumMethodInstanceByAddress 方法</span><span class="sxs-lookup"><span data-stu-id="f1380-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="f1380-103">列舉位址位移處開始此程序的方法執行的個體。</span><span class="sxs-lookup"><span data-stu-id="f1380-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f1380-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1380-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

### <a name="parameters"></a><span data-ttu-id="f1380-105">參數</span><span class="sxs-lookup"><span data-stu-id="f1380-105">Parameters</span></span>

<span data-ttu-id="f1380-106">`handle` [in]列舉的方法執行個體控制代碼。</span><span class="sxs-lookup"><span data-stu-id="f1380-106">`handle` [in] A handle for enumerating the method instances.</span></span>

<span data-ttu-id="f1380-107">`mod` [out]列舉的方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="f1380-107">`mod` [out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="f1380-108">備註</span><span class="sxs-lookup"><span data-stu-id="f1380-108">Remarks</span></span>

<span data-ttu-id="f1380-109">提供的方法是一部分`IXCLRDataProcess`介面，而對應的虛擬方法表的第 28 插槽。</span><span class="sxs-lookup"><span data-stu-id="f1380-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f1380-110">需求</span><span class="sxs-lookup"><span data-stu-id="f1380-110">Requirements</span></span>

<span data-ttu-id="f1380-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1380-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="f1380-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="f1380-112">**Header:** None</span></span>   
<span data-ttu-id="f1380-113">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="f1380-113">**Library:** None</span></span>   
<span data-ttu-id="f1380-114">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f1380-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="f1380-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1380-115">See Also</span></span>
- [<span data-ttu-id="f1380-116">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="f1380-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="f1380-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="f1380-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="f1380-118">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="f1380-118">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
