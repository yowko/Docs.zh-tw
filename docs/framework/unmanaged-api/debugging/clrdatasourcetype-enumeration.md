---
title: CLRDataSourceType 列舉
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d26cf45a0243d61757af5d9d0c00cf135ae15bdf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740864"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="3b674-102">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="3b674-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="3b674-103">提供 CLRDATA_IL_ADDRESS_MAP 結構所使用的值。</span><span class="sxs-lookup"><span data-stu-id="3b674-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3b674-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b674-104">Syntax</span></span>

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="3b674-105">成員</span><span class="sxs-lookup"><span data-stu-id="3b674-105">Members</span></span>

| <span data-ttu-id="3b674-106">成員</span><span class="sxs-lookup"><span data-stu-id="3b674-106">Member</span></span>                        | <span data-ttu-id="3b674-107">說明</span><span class="sxs-lookup"><span data-stu-id="3b674-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="3b674-108">表示沒有其他項目適用於</span><span class="sxs-lookup"><span data-stu-id="3b674-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="3b674-109">備註</span><span class="sxs-lookup"><span data-stu-id="3b674-109">Remarks</span></span>

<span data-ttu-id="3b674-110">這個列舉型別執行階段內，並且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="3b674-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="3b674-111">若要使用它，請定義列舉類型，如上面程式碼中所定義。</span><span class="sxs-lookup"><span data-stu-id="3b674-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="3b674-112">這也是別名`CLRDATA_ENUM`中所述[常見的資料型別](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="3b674-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="3b674-113">需求</span><span class="sxs-lookup"><span data-stu-id="3b674-113">Requirements</span></span>

<span data-ttu-id="3b674-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b674-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3b674-115">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="3b674-115">**Header:** None</span></span>  
<span data-ttu-id="3b674-116">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="3b674-116">**Library:** None</span></span>  
<span data-ttu-id="3b674-117">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3b674-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3b674-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b674-118">See also</span></span>

- [<span data-ttu-id="3b674-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="3b674-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="3b674-120">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="3b674-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
