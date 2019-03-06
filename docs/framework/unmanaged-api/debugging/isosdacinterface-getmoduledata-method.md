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
ms.openlocfilehash: b0edd459deaf68040e05209c6ecf2cb7cae12e8d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369951"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="17174-102">ISOSDacInterface::GetModuleData 方法</span><span class="sxs-lookup"><span data-stu-id="17174-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="17174-103">擷取對應至指定的位址在載入模組的資料。</span><span class="sxs-lookup"><span data-stu-id="17174-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="17174-104">語法</span><span class="sxs-lookup"><span data-stu-id="17174-104">Syntax</span></span>

```
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

### <a name="parameters"></a><span data-ttu-id="17174-105">參數</span><span class="sxs-lookup"><span data-stu-id="17174-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="17174-106">[in]要擷取的資訊之模組的位址。</span><span class="sxs-lookup"><span data-stu-id="17174-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="17174-107">[out][DacpModuleData 結構](dacpmoduledata-structure.md)來保存載入模組的資訊。</span><span class="sxs-lookup"><span data-stu-id="17174-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>


## <a name="remarks"></a><span data-ttu-id="17174-108">備註</span><span class="sxs-lookup"><span data-stu-id="17174-108">Remarks</span></span>

<span data-ttu-id="17174-109">提供的方法是一部分`ISOSDacInterface`介面，並對應至的虛擬方法表 13 的位置。</span><span class="sxs-lookup"><span data-stu-id="17174-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 13th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="17174-110">需求</span><span class="sxs-lookup"><span data-stu-id="17174-110">Requirements</span></span>

<span data-ttu-id="17174-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17174-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="17174-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="17174-112">**Header:** None</span></span>  
<span data-ttu-id="17174-113">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="17174-113">**Library:** None</span></span>  
<span data-ttu-id="17174-114">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="17174-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="17174-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17174-115">See also</span></span>

- [<span data-ttu-id="17174-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="17174-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="17174-117">ISOSDacInterface 介面</span><span class="sxs-lookup"><span data-stu-id="17174-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)