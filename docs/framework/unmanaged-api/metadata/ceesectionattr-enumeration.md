---
title: CeeSectionAttr 列舉
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b7f70162ae368934e1383683672fed86f9ce18c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441409"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="4a1bf-102">CeeSectionAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="4a1bf-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="4a1bf-103">提供值，指定以供區段屬性[ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="4a1bf-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a1bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="4a1bf-104">Syntax</span></span>  
  
```  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="4a1bf-105">成員</span><span class="sxs-lookup"><span data-stu-id="4a1bf-105">Members</span></span>  
  
|<span data-ttu-id="4a1bf-106">成員</span><span class="sxs-lookup"><span data-stu-id="4a1bf-106">Member</span></span>|<span data-ttu-id="4a1bf-107">描述</span><span class="sxs-lookup"><span data-stu-id="4a1bf-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="4a1bf-108">區段沒有任何屬性。</span><span class="sxs-lookup"><span data-stu-id="4a1bf-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="4a1bf-109">區段包含初始化可以只讀取，無法更新的資料。</span><span class="sxs-lookup"><span data-stu-id="4a1bf-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="4a1bf-110">區段包含初始化的資料可以讀取或更新。</span><span class="sxs-lookup"><span data-stu-id="4a1bf-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="4a1bf-111">區段包含允許讀取和執行的可執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a1bf-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a1bf-112">需求</span><span class="sxs-lookup"><span data-stu-id="4a1bf-112">Requirements</span></span>  
 <span data-ttu-id="4a1bf-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a1bf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a1bf-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4a1bf-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a1bf-115">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4a1bf-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a1bf-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a1bf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a1bf-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a1bf-117">See Also</span></span>  
 [<span data-ttu-id="4a1bf-118">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="4a1bf-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
