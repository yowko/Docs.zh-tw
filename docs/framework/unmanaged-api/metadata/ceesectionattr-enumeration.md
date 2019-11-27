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
ms.openlocfilehash: 97b28c961f43388679615ac0d5b19c4c69df1e3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444255"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="736f0-102">CeeSectionAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="736f0-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="736f0-103">提供值，指定區段的屬性供[ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)介面使用。</span><span class="sxs-lookup"><span data-stu-id="736f0-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="736f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="736f0-104">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="736f0-105">Members</span><span class="sxs-lookup"><span data-stu-id="736f0-105">Members</span></span>  
  
|<span data-ttu-id="736f0-106">成員</span><span class="sxs-lookup"><span data-stu-id="736f0-106">Member</span></span>|<span data-ttu-id="736f0-107">描述</span><span class="sxs-lookup"><span data-stu-id="736f0-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="736f0-108">區段沒有屬性。</span><span class="sxs-lookup"><span data-stu-id="736f0-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="736f0-109">區段包含只能讀取、未更新的初始化資料。</span><span class="sxs-lookup"><span data-stu-id="736f0-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="736f0-110">區段包含可讀取或更新的初始化資料。</span><span class="sxs-lookup"><span data-stu-id="736f0-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="736f0-111">區段包含允許讀取和執行的可執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="736f0-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="736f0-112">需求</span><span class="sxs-lookup"><span data-stu-id="736f0-112">Requirements</span></span>  
 <span data-ttu-id="736f0-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="736f0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="736f0-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="736f0-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="736f0-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="736f0-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="736f0-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="736f0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="736f0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="736f0-117">See also</span></span>

- [<span data-ttu-id="736f0-118">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="736f0-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
