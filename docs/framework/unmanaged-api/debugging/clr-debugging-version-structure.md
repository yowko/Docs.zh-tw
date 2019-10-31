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
ms.openlocfilehash: 651b916a0e3ca178432094428611f9bcc8f0fd17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132424"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="f99a7-102">CLR_DEBUGGING_VERSION 結構</span><span class="sxs-lookup"><span data-stu-id="f99a7-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="f99a7-103">定義用來偵錯之工具通用語言執行平台 (CLR) 的產品版本。</span><span class="sxs-lookup"><span data-stu-id="f99a7-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f99a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="f99a7-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f99a7-105">Members</span><span class="sxs-lookup"><span data-stu-id="f99a7-105">Members</span></span>  
  
|<span data-ttu-id="f99a7-106">成員</span><span class="sxs-lookup"><span data-stu-id="f99a7-106">Member</span></span>|<span data-ttu-id="f99a7-107">描述</span><span class="sxs-lookup"><span data-stu-id="f99a7-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="f99a7-108">結構版本號碼</span><span class="sxs-lookup"><span data-stu-id="f99a7-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="f99a7-109">主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f99a7-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="f99a7-110">次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f99a7-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="f99a7-111">組建編號。</span><span class="sxs-lookup"><span data-stu-id="f99a7-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="f99a7-112">修訂編號。</span><span class="sxs-lookup"><span data-stu-id="f99a7-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f99a7-113">備註</span><span class="sxs-lookup"><span data-stu-id="f99a7-113">Remarks</span></span>  
 <span data-ttu-id="f99a7-114">`CLR_DEBUGGING_VERSION` 結構與 COR_VERSION 結構相同，不過，`CLR_DEBUGGING_VERSION` 結構會提供額外的結構版本欄位（`wStructVersion`）。</span><span class="sxs-lookup"><span data-stu-id="f99a7-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="f99a7-115">目前，此欄位必須設定為零。</span><span class="sxs-lookup"><span data-stu-id="f99a7-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f99a7-116">需求</span><span class="sxs-lookup"><span data-stu-id="f99a7-116">Requirements</span></span>  
 <span data-ttu-id="f99a7-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f99a7-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f99a7-118">**標頭：** Cordebug.h .idl</span><span class="sxs-lookup"><span data-stu-id="f99a7-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="f99a7-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f99a7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f99a7-120">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f99a7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f99a7-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="f99a7-121">See also</span></span>

- [<span data-ttu-id="f99a7-122">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="f99a7-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="f99a7-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="f99a7-123">Debugging</span></span>](index.md)
