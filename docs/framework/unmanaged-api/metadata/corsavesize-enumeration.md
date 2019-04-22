---
title: CorSaveSize 列舉
ms.date: 03/30/2017
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc36468a2016822e884ec3a36a23c75477a00a2d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217194"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="61f2c-102">CorSaveSize 列舉</span><span class="sxs-lookup"><span data-stu-id="61f2c-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="61f2c-103">包含值，這些值表示在查詢儲存作業的大小時所需的精確度等級。</span><span class="sxs-lookup"><span data-stu-id="61f2c-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61f2c-104">語法</span><span class="sxs-lookup"><span data-stu-id="61f2c-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="61f2c-105">成員</span><span class="sxs-lookup"><span data-stu-id="61f2c-105">Members</span></span>  
  
|<span data-ttu-id="61f2c-106">成員</span><span class="sxs-lookup"><span data-stu-id="61f2c-106">Member</span></span>|<span data-ttu-id="61f2c-107">描述</span><span class="sxs-lookup"><span data-stu-id="61f2c-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="61f2c-108">指定傳回的值應該完全一樣。</span><span class="sxs-lookup"><span data-stu-id="61f2c-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="61f2c-109">指定應該估計的傳回值。</span><span class="sxs-lookup"><span data-stu-id="61f2c-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="61f2c-110">指定應移除捨棄的型別。</span><span class="sxs-lookup"><span data-stu-id="61f2c-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61f2c-111">需求</span><span class="sxs-lookup"><span data-stu-id="61f2c-111">Requirements</span></span>  
 <span data-ttu-id="61f2c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61f2c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61f2c-113">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="61f2c-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="61f2c-114">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="61f2c-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="61f2c-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61f2c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61f2c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61f2c-116">See also</span></span>

- [<span data-ttu-id="61f2c-117">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="61f2c-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
