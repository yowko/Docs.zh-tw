---
title: CLR_DEBUGGING_VERSION 結構
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4528ccd77fed2ea2a9b2d08243ffa1535bfad1ae
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274080"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="ce383-102">CLR_DEBUGGING_VERSION 結構</span><span class="sxs-lookup"><span data-stu-id="ce383-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="ce383-103">定義用來偵錯之工具通用語言執行平台 (CLR) 的產品版本。</span><span class="sxs-lookup"><span data-stu-id="ce383-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce383-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce383-104">Syntax</span></span>  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a><span data-ttu-id="ce383-105">成員</span><span class="sxs-lookup"><span data-stu-id="ce383-105">Members</span></span>  
  
|<span data-ttu-id="ce383-106">成員</span><span class="sxs-lookup"><span data-stu-id="ce383-106">Member</span></span>|<span data-ttu-id="ce383-107">描述</span><span class="sxs-lookup"><span data-stu-id="ce383-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="ce383-108">結構版本號碼</span><span class="sxs-lookup"><span data-stu-id="ce383-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="ce383-109">主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="ce383-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="ce383-110">次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="ce383-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="ce383-111">組建編號。</span><span class="sxs-lookup"><span data-stu-id="ce383-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="ce383-112">修訂編號。</span><span class="sxs-lookup"><span data-stu-id="ce383-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce383-113">備註</span><span class="sxs-lookup"><span data-stu-id="ce383-113">Remarks</span></span>  
 <span data-ttu-id="ce383-114">結構與 COR_VERSION 結構相同，不過`CLR_DEBUGGING_VERSION` ，結構會提供其他結構版本欄位（`wStructVersion`）。 `CLR_DEBUGGING_VERSION`</span><span class="sxs-lookup"><span data-stu-id="ce383-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="ce383-115">目前，此欄位必須設定為零。</span><span class="sxs-lookup"><span data-stu-id="ce383-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce383-116">需求</span><span class="sxs-lookup"><span data-stu-id="ce383-116">Requirements</span></span>  
 <span data-ttu-id="ce383-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce383-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce383-118">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="ce383-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="ce383-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce383-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce383-120">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce383-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce383-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce383-121">See also</span></span>

- [<span data-ttu-id="ce383-122">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="ce383-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="ce383-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="ce383-123">Debugging</span></span>](index.md)
