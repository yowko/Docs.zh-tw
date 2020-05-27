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
ms.openlocfilehash: 84791eba7c95d3278bd4650bd7d660e98fcb79d8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008910"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="55b97-102">CVStruct 結構</span><span class="sxs-lookup"><span data-stu-id="55b97-102">CVStruct Structure</span></span>
<span data-ttu-id="55b97-103">包含在安裝模組或複合映像時，所使用的資訊。</span><span class="sxs-lookup"><span data-stu-id="55b97-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55b97-104">語法</span><span class="sxs-lookup"><span data-stu-id="55b97-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="55b97-105">成員</span><span class="sxs-lookup"><span data-stu-id="55b97-105">Members</span></span>  
  
|<span data-ttu-id="55b97-106">成員</span><span class="sxs-lookup"><span data-stu-id="55b97-106">Member</span></span>|<span data-ttu-id="55b97-107">描述</span><span class="sxs-lookup"><span data-stu-id="55b97-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="55b97-108">主要</span><span class="sxs-lookup"><span data-stu-id="55b97-108">Major</span></span>|<span data-ttu-id="55b97-109">主要版本組建編號。</span><span class="sxs-lookup"><span data-stu-id="55b97-109">Major version build number.</span></span>|  
|<span data-ttu-id="55b97-110">Minor</span><span class="sxs-lookup"><span data-stu-id="55b97-110">Minor</span></span>|<span data-ttu-id="55b97-111">次要版本組建編號。</span><span class="sxs-lookup"><span data-stu-id="55b97-111">Minor version build number.</span></span>|  
|<span data-ttu-id="55b97-112">Sub</span><span class="sxs-lookup"><span data-stu-id="55b97-112">Sub</span></span>|<span data-ttu-id="55b97-113">子組建編號。</span><span class="sxs-lookup"><span data-stu-id="55b97-113">Sub-build number.</span></span>|  
|<span data-ttu-id="55b97-114">Build</span><span class="sxs-lookup"><span data-stu-id="55b97-114">Build</span></span>|<span data-ttu-id="55b97-115">組建編號。</span><span class="sxs-lookup"><span data-stu-id="55b97-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55b97-116">需求</span><span class="sxs-lookup"><span data-stu-id="55b97-116">Requirements</span></span>  
 <span data-ttu-id="55b97-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="55b97-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55b97-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="55b97-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="55b97-119">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="55b97-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="55b97-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55b97-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55b97-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55b97-121">See also</span></span>

- [<span data-ttu-id="55b97-122">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="55b97-122">Metadata Structures</span></span>](metadata-structures.md)
