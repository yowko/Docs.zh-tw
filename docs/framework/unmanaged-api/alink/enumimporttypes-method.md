---
title: EnumImportTypes 方法
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448730"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="41ea7-102">EnumImportTypes 方法</span><span class="sxs-lookup"><span data-stu-id="41ea7-102">EnumImportTypes Method</span></span>

<span data-ttu-id="41ea7-103">列舉每個範圍中的每個類型。</span><span class="sxs-lookup"><span data-stu-id="41ea7-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="41ea7-104">語法</span><span class="sxs-lookup"><span data-stu-id="41ea7-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="41ea7-105">參數</span><span class="sxs-lookup"><span data-stu-id="41ea7-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="41ea7-106">列舉值的控制碼。</span><span class="sxs-lookup"><span data-stu-id="41ea7-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="41ea7-107">要取出的類型數目上限。</span><span class="sxs-lookup"><span data-stu-id="41ea7-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="41ea7-108">接收類型標記，而不是超過 `dwMax`。</span><span class="sxs-lookup"><span data-stu-id="41ea7-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="41ea7-109">在 `aTypeDefs`中，接收類型的實際數目。</span><span class="sxs-lookup"><span data-stu-id="41ea7-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="41ea7-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="41ea7-110">Return Value</span></span>

<span data-ttu-id="41ea7-111">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="41ea7-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="41ea7-112">需求</span><span class="sxs-lookup"><span data-stu-id="41ea7-112">Requirements</span></span>

<span data-ttu-id="41ea7-113">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="41ea7-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="41ea7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41ea7-114">See also</span></span>

- [<span data-ttu-id="41ea7-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="41ea7-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="41ea7-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="41ea7-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="41ea7-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="41ea7-117">ALink API</span></span>](index.md)
