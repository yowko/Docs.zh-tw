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
ms.openlocfilehash: 8a4cc17bdcaea5099d0d2b0195ae4fa28e3d4744
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744595"
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="ee569-102">CorImportOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="ee569-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="ee569-103">包含旗標值，這些值可控制在匯入目前範圍之外的組件期間所發生的行為。</span><span class="sxs-lookup"><span data-stu-id="ee569-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee569-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee569-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ee569-105">成員</span><span class="sxs-lookup"><span data-stu-id="ee569-105">Members</span></span>  
  
|<span data-ttu-id="ee569-106">成員</span><span class="sxs-lookup"><span data-stu-id="ee569-106">Member</span></span>|<span data-ttu-id="ee569-107">描述</span><span class="sxs-lookup"><span data-stu-id="ee569-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="ee569-108">表示預設行為，也就是略過已刪除的記錄。</span><span class="sxs-lookup"><span data-stu-id="ee569-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="ee569-109">指出應該要列舉所有的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ee569-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="ee569-110">指出應該要列舉所有的 Typedef，包括已刪除的。</span><span class="sxs-lookup"><span data-stu-id="ee569-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="ee569-111">表示所有 MethodDefs，包括已刪除的應該要都列舉。</span><span class="sxs-lookup"><span data-stu-id="ee569-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="ee569-112">表示所有 FieldDefs，包括已刪除的應該要都列舉。</span><span class="sxs-lookup"><span data-stu-id="ee569-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="ee569-113">表示所有 PropertyDefs，包括已刪除的應該要都列舉。</span><span class="sxs-lookup"><span data-stu-id="ee569-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="ee569-114">表示所有 EventDefs，包括已刪除的應該要都列舉。</span><span class="sxs-lookup"><span data-stu-id="ee569-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="ee569-115">指出應該要列舉所有的自訂屬性，包括已刪除的。</span><span class="sxs-lookup"><span data-stu-id="ee569-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="ee569-116">表示所有匯出的類型，包括已刪除的應該要列舉。</span><span class="sxs-lookup"><span data-stu-id="ee569-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee569-117">需求</span><span class="sxs-lookup"><span data-stu-id="ee569-117">Requirements</span></span>  
 <span data-ttu-id="ee569-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee569-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee569-119">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ee569-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ee569-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee569-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee569-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee569-121">See also</span></span>
- [<span data-ttu-id="ee569-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="ee569-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
