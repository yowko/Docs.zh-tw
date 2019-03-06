---
title: CorThreadSafetyOptions 列舉
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d71d2a5b3007d4e877900443af426a9643b29125
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360430"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="49132-102">CorThreadSafetyOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="49132-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="49132-103">指定旗標，以選取執行緒安全的選項。</span><span class="sxs-lookup"><span data-stu-id="49132-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="49132-104">語法</span><span class="sxs-lookup"><span data-stu-id="49132-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="49132-105">成員</span><span class="sxs-lookup"><span data-stu-id="49132-105">Members</span></span>

|<span data-ttu-id="49132-106">成員</span><span class="sxs-lookup"><span data-stu-id="49132-106">Member</span></span>|<span data-ttu-id="49132-107">描述</span><span class="sxs-lookup"><span data-stu-id="49132-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="49132-108">預設值。</span><span class="sxs-lookup"><span data-stu-id="49132-108">Default value.</span></span> <span data-ttu-id="49132-109">與 `MDThreadSafetyOff` 相同。</span><span class="sxs-lookup"><span data-stu-id="49132-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="49132-110">表示不能設定的讀取器/寫入器鎖定。</span><span class="sxs-lookup"><span data-stu-id="49132-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="49132-111">表示，您可以設定的讀取器/寫入器鎖定。</span><span class="sxs-lookup"><span data-stu-id="49132-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="49132-112">需求</span><span class="sxs-lookup"><span data-stu-id="49132-112">Requirements</span></span>

<span data-ttu-id="49132-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49132-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="49132-114">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="49132-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="49132-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49132-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="49132-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49132-116">See also</span></span>

- [<span data-ttu-id="49132-117">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="49132-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
