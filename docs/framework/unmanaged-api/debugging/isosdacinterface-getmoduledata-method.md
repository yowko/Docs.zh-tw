---
title: ISOSDacInterface::GetModuleData 方法
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 128af261c429228c97d952f1f8d382f46306f711
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229312"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="99d50-102">ISOSDacInterface::GetModuleData 方法</span><span class="sxs-lookup"><span data-stu-id="99d50-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="99d50-103">擷取對應至指定的位址在載入模組的資料。</span><span class="sxs-lookup"><span data-stu-id="99d50-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="99d50-104">語法</span><span class="sxs-lookup"><span data-stu-id="99d50-104">Syntax</span></span>

```
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="99d50-105">參數</span><span class="sxs-lookup"><span data-stu-id="99d50-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="99d50-106">[in]要擷取的資訊之模組的位址。</span><span class="sxs-lookup"><span data-stu-id="99d50-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="99d50-107">[out][DacpModuleData 結構](dacpmoduledata-structure.md)來保存載入模組的資訊。</span><span class="sxs-lookup"><span data-stu-id="99d50-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="99d50-108">備註</span><span class="sxs-lookup"><span data-stu-id="99d50-108">Remarks</span></span>

<span data-ttu-id="99d50-109">提供的方法是一部分`ISOSDacInterface`介面，並對應至的虛擬方法表 13 的位置。</span><span class="sxs-lookup"><span data-stu-id="99d50-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 13th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="99d50-110">需求</span><span class="sxs-lookup"><span data-stu-id="99d50-110">Requirements</span></span>

<span data-ttu-id="99d50-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="99d50-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="99d50-112">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="99d50-112">**Header:** None</span></span>  
<span data-ttu-id="99d50-113">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="99d50-113">**Library:** None</span></span>  
**<span data-ttu-id="99d50-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="99d50-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="99d50-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99d50-115">See also</span></span>

- [<span data-ttu-id="99d50-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="99d50-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="99d50-117">ISOSDacInterface 介面</span><span class="sxs-lookup"><span data-stu-id="99d50-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)