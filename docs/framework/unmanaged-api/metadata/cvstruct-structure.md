---
title: CVStruct 結構
ms.date: 03/30/2017
api_name:
- CVStruct
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CVStruct
helpviewer_keywords:
- CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a5f06b3f79fed5dac5a6f07650e4fabd0aa5867
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142164"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="749e9-102">CVStruct 結構</span><span class="sxs-lookup"><span data-stu-id="749e9-102">CVStruct Structure</span></span>
<span data-ttu-id="749e9-103">包含在安裝模組或複合映像時，所使用的資訊。</span><span class="sxs-lookup"><span data-stu-id="749e9-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="749e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="749e9-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="749e9-105">成員</span><span class="sxs-lookup"><span data-stu-id="749e9-105">Members</span></span>  
  
|<span data-ttu-id="749e9-106">成員</span><span class="sxs-lookup"><span data-stu-id="749e9-106">Member</span></span>|<span data-ttu-id="749e9-107">描述</span><span class="sxs-lookup"><span data-stu-id="749e9-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="749e9-108">主要</span><span class="sxs-lookup"><span data-stu-id="749e9-108">Major</span></span>|<span data-ttu-id="749e9-109">主要版本的組建編號。</span><span class="sxs-lookup"><span data-stu-id="749e9-109">Major version build number.</span></span>|  
|<span data-ttu-id="749e9-110">次要</span><span class="sxs-lookup"><span data-stu-id="749e9-110">Minor</span></span>|<span data-ttu-id="749e9-111">次要版本組建編號。</span><span class="sxs-lookup"><span data-stu-id="749e9-111">Minor version build number.</span></span>|  
|<span data-ttu-id="749e9-112">Sub</span><span class="sxs-lookup"><span data-stu-id="749e9-112">Sub</span></span>|<span data-ttu-id="749e9-113">子組建編號。</span><span class="sxs-lookup"><span data-stu-id="749e9-113">Sub-build number.</span></span>|  
|<span data-ttu-id="749e9-114">組建</span><span class="sxs-lookup"><span data-stu-id="749e9-114">Build</span></span>|<span data-ttu-id="749e9-115">組建編號。</span><span class="sxs-lookup"><span data-stu-id="749e9-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="749e9-116">需求</span><span class="sxs-lookup"><span data-stu-id="749e9-116">Requirements</span></span>  
 <span data-ttu-id="749e9-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="749e9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="749e9-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="749e9-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="749e9-119">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="749e9-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="749e9-120">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="749e9-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="749e9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="749e9-121">See also</span></span>

- [<span data-ttu-id="749e9-122">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="749e9-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
