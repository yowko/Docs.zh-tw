---
title: "CLR_DEBUGGING_VERSION 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 092024f3f4e6fc1bc923ae2a299c5d9c21f1b1b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="39cc1-102">CLR_DEBUGGING_VERSION 結構</span><span class="sxs-lookup"><span data-stu-id="39cc1-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="39cc1-103">定義用來偵錯之工具通用語言執行平台 (CLR) 的產品版本。</span><span class="sxs-lookup"><span data-stu-id="39cc1-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39cc1-104">語法</span><span class="sxs-lookup"><span data-stu-id="39cc1-104">Syntax</span></span>  
  
```  
Typedef struct _CLR_DEBUGGING_VERSION  
{  
WORD wStructVersion;  
WORD wMajor;   
WORD wMinor;  
WORD wBuild;  
WORD wRevision;  
}  CLR_DEBUGGING_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="39cc1-105">成員</span><span class="sxs-lookup"><span data-stu-id="39cc1-105">Members</span></span>  
  
|<span data-ttu-id="39cc1-106">成員</span><span class="sxs-lookup"><span data-stu-id="39cc1-106">Member</span></span>|<span data-ttu-id="39cc1-107">描述</span><span class="sxs-lookup"><span data-stu-id="39cc1-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="39cc1-108">結構版本號碼</span><span class="sxs-lookup"><span data-stu-id="39cc1-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="39cc1-109">主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="39cc1-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="39cc1-110">次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="39cc1-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="39cc1-111">組建編號。</span><span class="sxs-lookup"><span data-stu-id="39cc1-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="39cc1-112">修訂編號。</span><span class="sxs-lookup"><span data-stu-id="39cc1-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39cc1-113">備註</span><span class="sxs-lookup"><span data-stu-id="39cc1-113">Remarks</span></span>  
 <span data-ttu-id="39cc1-114">`CLR_DEBUGGING_VERSION`結構等同於 COR_VERSION 結構中，不過，`CLR_DEBUGGING_VERSION`結構提供額外的結構版本 欄位 (`wStructVersion`)。</span><span class="sxs-lookup"><span data-stu-id="39cc1-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="39cc1-115">目前，此欄位必須設定為零。</span><span class="sxs-lookup"><span data-stu-id="39cc1-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39cc1-116">需求</span><span class="sxs-lookup"><span data-stu-id="39cc1-116">Requirements</span></span>  
 <span data-ttu-id="39cc1-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39cc1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39cc1-118">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="39cc1-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="39cc1-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39cc1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39cc1-120">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39cc1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39cc1-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="39cc1-121">See Also</span></span>  
 [<span data-ttu-id="39cc1-122">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="39cc1-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="39cc1-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="39cc1-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
