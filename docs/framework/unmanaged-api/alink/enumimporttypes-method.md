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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cd154ac90418dd0f6f476151686ff670c01c98c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632238"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="cd228-102">EnumImportTypes 方法</span><span class="sxs-lookup"><span data-stu-id="cd228-102">EnumImportTypes Method</span></span>

<span data-ttu-id="cd228-103">列舉每個範圍中的每個型別。</span><span class="sxs-lookup"><span data-stu-id="cd228-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd228-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd228-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="cd228-105">參數</span><span class="sxs-lookup"><span data-stu-id="cd228-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="cd228-106">列舉值的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="cd228-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="cd228-107">擷取類型的最大數目。</span><span class="sxs-lookup"><span data-stu-id="cd228-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="cd228-108">接收類型的語彙基元，不能超過`dwMax`。</span><span class="sxs-lookup"><span data-stu-id="cd228-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="cd228-109">接收輸入的實際數目`aTypeDefs`。</span><span class="sxs-lookup"><span data-stu-id="cd228-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="cd228-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="cd228-110">Return Value</span></span>

<span data-ttu-id="cd228-111">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="cd228-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="cd228-112">需求</span><span class="sxs-lookup"><span data-stu-id="cd228-112">Requirements</span></span>

<span data-ttu-id="cd228-113">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="cd228-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="cd228-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd228-114">See also</span></span>

- [<span data-ttu-id="cd228-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="cd228-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="cd228-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="cd228-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="cd228-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="cd228-117">ALink API</span></span>](index.md)
