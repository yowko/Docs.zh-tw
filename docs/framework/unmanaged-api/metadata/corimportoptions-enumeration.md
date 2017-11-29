---
title: "CorImportOptions 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorImportOptions
api_location: mscoree.dll
api_type: COM
f1_keywords: CorImportOptions
helpviewer_keywords: CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3e014443945574cff2733e5bc5d992691acc3fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="7498a-102">CorImportOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="7498a-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="7498a-103">包含旗標值，這些值可控制在匯入目前範圍之外的組件期間所發生的行為。</span><span class="sxs-lookup"><span data-stu-id="7498a-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7498a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7498a-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="7498a-105">成員</span><span class="sxs-lookup"><span data-stu-id="7498a-105">Members</span></span>  
  
|<span data-ttu-id="7498a-106">成員</span><span class="sxs-lookup"><span data-stu-id="7498a-106">Member</span></span>|<span data-ttu-id="7498a-107">說明</span><span class="sxs-lookup"><span data-stu-id="7498a-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="7498a-108">表示預設行為，也就是略過已刪除的記錄。</span><span class="sxs-lookup"><span data-stu-id="7498a-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="7498a-109">表示應該列舉所有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7498a-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="7498a-110">表示應該列舉所有的 Typedef，包括已刪除的。</span><span class="sxs-lookup"><span data-stu-id="7498a-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="7498a-111">表示應該列舉所有 MethodDefs，包括已刪除的。</span><span class="sxs-lookup"><span data-stu-id="7498a-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="7498a-112">表示應該列舉所有 FieldDefs，包括已刪除的。</span><span class="sxs-lookup"><span data-stu-id="7498a-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="7498a-113">表示應該列舉所有 PropertyDefs，包括已刪除的。</span><span class="sxs-lookup"><span data-stu-id="7498a-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="7498a-114">表示應該列舉所有 EventDefs，包括已刪除的。</span><span class="sxs-lookup"><span data-stu-id="7498a-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="7498a-115">表示應該列舉所有的自訂屬性，包括已刪除的。</span><span class="sxs-lookup"><span data-stu-id="7498a-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="7498a-116">表示應該列舉所有的匯出的類型，包括已刪除的。</span><span class="sxs-lookup"><span data-stu-id="7498a-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7498a-117">需求</span><span class="sxs-lookup"><span data-stu-id="7498a-117">Requirements</span></span>  
 <span data-ttu-id="7498a-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7498a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7498a-119">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="7498a-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7498a-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7498a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7498a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7498a-121">See Also</span></span>  
 [<span data-ttu-id="7498a-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="7498a-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
