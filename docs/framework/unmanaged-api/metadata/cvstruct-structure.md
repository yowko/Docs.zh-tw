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
ms.openlocfilehash: 19ee3097dfe80ba9dcbdaf316db0fd165b50abc6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436422"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="e0e76-102">CVStruct 結構</span><span class="sxs-lookup"><span data-stu-id="e0e76-102">CVStruct Structure</span></span>
<span data-ttu-id="e0e76-103">包含在安裝模組或複合映像時，所使用的資訊。</span><span class="sxs-lookup"><span data-stu-id="e0e76-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0e76-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0e76-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="e0e76-105">Members</span><span class="sxs-lookup"><span data-stu-id="e0e76-105">Members</span></span>  
  
|<span data-ttu-id="e0e76-106">成員</span><span class="sxs-lookup"><span data-stu-id="e0e76-106">Member</span></span>|<span data-ttu-id="e0e76-107">描述</span><span class="sxs-lookup"><span data-stu-id="e0e76-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e0e76-108">重大</span><span class="sxs-lookup"><span data-stu-id="e0e76-108">Major</span></span>|<span data-ttu-id="e0e76-109">主要版本組建編號。</span><span class="sxs-lookup"><span data-stu-id="e0e76-109">Major version build number.</span></span>|  
|<span data-ttu-id="e0e76-110">微幅</span><span class="sxs-lookup"><span data-stu-id="e0e76-110">Minor</span></span>|<span data-ttu-id="e0e76-111">次要版本組建編號。</span><span class="sxs-lookup"><span data-stu-id="e0e76-111">Minor version build number.</span></span>|  
|<span data-ttu-id="e0e76-112">訂閱</span><span class="sxs-lookup"><span data-stu-id="e0e76-112">Sub</span></span>|<span data-ttu-id="e0e76-113">子組建編號。</span><span class="sxs-lookup"><span data-stu-id="e0e76-113">Sub-build number.</span></span>|  
|<span data-ttu-id="e0e76-114">組建</span><span class="sxs-lookup"><span data-stu-id="e0e76-114">Build</span></span>|<span data-ttu-id="e0e76-115">組建編號。</span><span class="sxs-lookup"><span data-stu-id="e0e76-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0e76-116">需求</span><span class="sxs-lookup"><span data-stu-id="e0e76-116">Requirements</span></span>  
 <span data-ttu-id="e0e76-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0e76-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0e76-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="e0e76-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0e76-119">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="e0e76-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0e76-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0e76-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0e76-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0e76-121">See also</span></span>

- [<span data-ttu-id="e0e76-122">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="e0e76-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
