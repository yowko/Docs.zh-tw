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
ms.openlocfilehash: 23b567e4119578fba2f8cd4ba47f66dcf56a3878
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496842"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="f073a-102">IXCLRDataProcess::EnumMethodInstanceByAddress 方法</span><span class="sxs-lookup"><span data-stu-id="f073a-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="f073a-103">列舉位址位移處開始此程序的方法執行的個體。</span><span class="sxs-lookup"><span data-stu-id="f073a-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f073a-104">語法</span><span class="sxs-lookup"><span data-stu-id="f073a-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="f073a-105">參數</span><span class="sxs-lookup"><span data-stu-id="f073a-105">Parameters</span></span>

`handle`\
<span data-ttu-id="f073a-106">[in]列舉的方法執行個體控制代碼。</span><span class="sxs-lookup"><span data-stu-id="f073a-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="f073a-107">[out]列舉的方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="f073a-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="f073a-108">備註</span><span class="sxs-lookup"><span data-stu-id="f073a-108">Remarks</span></span>

<span data-ttu-id="f073a-109">提供的方法是一部分`IXCLRDataProcess`介面，而對應的虛擬方法表的第 28 插槽。</span><span class="sxs-lookup"><span data-stu-id="f073a-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f073a-110">需求</span><span class="sxs-lookup"><span data-stu-id="f073a-110">Requirements</span></span>

<span data-ttu-id="f073a-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f073a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="f073a-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="f073a-112">**Header:** None</span></span>   
<span data-ttu-id="f073a-113">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="f073a-113">**Library:** None</span></span>   
<span data-ttu-id="f073a-114">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f073a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="f073a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f073a-115">See also</span></span>
- [<span data-ttu-id="f073a-116">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="f073a-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="f073a-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="f073a-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="f073a-118">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="f073a-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
