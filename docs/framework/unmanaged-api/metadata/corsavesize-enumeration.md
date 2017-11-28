---
title: "CorSaveSize 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSaveSize
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSaveSize
helpviewer_keywords: CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 34d4d42c7cf385bca77de37dce52689778aa5b1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="e603e-102">CorSaveSize 列舉</span><span class="sxs-lookup"><span data-stu-id="e603e-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="e603e-103">包含值，這些值表示在查詢儲存作業的大小時所需的精確度等級。</span><span class="sxs-lookup"><span data-stu-id="e603e-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e603e-104">語法</span><span class="sxs-lookup"><span data-stu-id="e603e-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="e603e-105">成員</span><span class="sxs-lookup"><span data-stu-id="e603e-105">Members</span></span>  
  
|<span data-ttu-id="e603e-106">成員</span><span class="sxs-lookup"><span data-stu-id="e603e-106">Member</span></span>|<span data-ttu-id="e603e-107">說明</span><span class="sxs-lookup"><span data-stu-id="e603e-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="e603e-108">指定傳回的值應該完全一樣。</span><span class="sxs-lookup"><span data-stu-id="e603e-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="e603e-109">指定應該估計的傳回值。</span><span class="sxs-lookup"><span data-stu-id="e603e-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="e603e-110">指定應移除捨棄的型別。</span><span class="sxs-lookup"><span data-stu-id="e603e-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e603e-111">需求</span><span class="sxs-lookup"><span data-stu-id="e603e-111">Requirements</span></span>  
 <span data-ttu-id="e603e-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e603e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e603e-113">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e603e-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e603e-114">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e603e-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e603e-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e603e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e603e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e603e-116">See Also</span></span>  
 [<span data-ttu-id="e603e-117">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="e603e-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
