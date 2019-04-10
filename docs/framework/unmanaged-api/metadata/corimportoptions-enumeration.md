---
title: CorImportOptions 列舉
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2f71a277484adbbfe3628222c635528cdab03e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156126"
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="e95d9-102">CorImportOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="e95d9-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="e95d9-103">包含旗標值，這些值可控制在匯入目前範圍之外的組件期間所發生的行為。</span><span class="sxs-lookup"><span data-stu-id="e95d9-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e95d9-104">語法</span><span class="sxs-lookup"><span data-stu-id="e95d9-104">Syntax</span></span>  
  
```  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="e95d9-105">成員</span><span class="sxs-lookup"><span data-stu-id="e95d9-105">Members</span></span>  
  
|<span data-ttu-id="e95d9-106">成員</span><span class="sxs-lookup"><span data-stu-id="e95d9-106">Member</span></span>|<span data-ttu-id="e95d9-107">描述</span><span class="sxs-lookup"><span data-stu-id="e95d9-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="e95d9-108">表示預設行為，也就是略過已刪除的記錄。</span><span class="sxs-lookup"><span data-stu-id="e95d9-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="e95d9-109">指出應該要列舉所有的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e95d9-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="e95d9-110">指出應該要列舉所有的 Typedef，包括已刪除的。</span><span class="sxs-lookup"><span data-stu-id="e95d9-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="e95d9-111">表示所有 MethodDefs，包括已刪除的應該要都列舉。</span><span class="sxs-lookup"><span data-stu-id="e95d9-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="e95d9-112">表示所有 FieldDefs，包括已刪除的應該要都列舉。</span><span class="sxs-lookup"><span data-stu-id="e95d9-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="e95d9-113">表示所有 PropertyDefs，包括已刪除的應該要都列舉。</span><span class="sxs-lookup"><span data-stu-id="e95d9-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="e95d9-114">表示所有 EventDefs，包括已刪除的應該要都列舉。</span><span class="sxs-lookup"><span data-stu-id="e95d9-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="e95d9-115">指出應該要列舉所有的自訂屬性，包括已刪除的。</span><span class="sxs-lookup"><span data-stu-id="e95d9-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="e95d9-116">表示所有匯出的類型，包括已刪除的應該要列舉。</span><span class="sxs-lookup"><span data-stu-id="e95d9-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e95d9-117">需求</span><span class="sxs-lookup"><span data-stu-id="e95d9-117">Requirements</span></span>  
 <span data-ttu-id="e95d9-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e95d9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e95d9-119">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e95d9-119">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="e95d9-120">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="e95d9-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e95d9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e95d9-121">See also</span></span>

- [<span data-ttu-id="e95d9-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="e95d9-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
