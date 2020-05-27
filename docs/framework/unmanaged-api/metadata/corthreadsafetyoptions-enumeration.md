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
ms.openlocfilehash: 8c0527a7bc3cde7344bf809dc8e6f5a3fac04852
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007503"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="e1907-102">CorThreadSafetyOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="e1907-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="e1907-103">指定旗標，以選取執行緒安全的選項。</span><span class="sxs-lookup"><span data-stu-id="e1907-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="e1907-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1907-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="e1907-105">成員</span><span class="sxs-lookup"><span data-stu-id="e1907-105">Members</span></span>

|<span data-ttu-id="e1907-106">成員</span><span class="sxs-lookup"><span data-stu-id="e1907-106">Member</span></span>|<span data-ttu-id="e1907-107">描述</span><span class="sxs-lookup"><span data-stu-id="e1907-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="e1907-108">預設值。</span><span class="sxs-lookup"><span data-stu-id="e1907-108">Default value.</span></span> <span data-ttu-id="e1907-109">與 `MDThreadSafetyOff` 相同。</span><span class="sxs-lookup"><span data-stu-id="e1907-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="e1907-110">表示無法設定讀取器/寫入器鎖定。</span><span class="sxs-lookup"><span data-stu-id="e1907-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="e1907-111">表示可以設定讀取器/寫入器鎖定。</span><span class="sxs-lookup"><span data-stu-id="e1907-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="e1907-112">需求</span><span class="sxs-lookup"><span data-stu-id="e1907-112">Requirements</span></span>

<span data-ttu-id="e1907-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1907-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="e1907-114">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="e1907-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="e1907-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1907-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e1907-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1907-116">See also</span></span>

- [<span data-ttu-id="e1907-117">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="e1907-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
