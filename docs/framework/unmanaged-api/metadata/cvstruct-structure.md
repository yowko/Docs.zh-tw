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
ms.openlocfilehash: db36b94fafe20b58b9bcbb886b8d285326960f67
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715572"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="ba97c-102">CVStruct 結構</span><span class="sxs-lookup"><span data-stu-id="ba97c-102">CVStruct Structure</span></span>

<span data-ttu-id="ba97c-103">包含在安裝模組或複合映像時，所使用的資訊。</span><span class="sxs-lookup"><span data-stu-id="ba97c-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba97c-104">語法</span><span class="sxs-lookup"><span data-stu-id="ba97c-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="ba97c-105">成員</span><span class="sxs-lookup"><span data-stu-id="ba97c-105">Members</span></span>  
  
|<span data-ttu-id="ba97c-106">member</span><span class="sxs-lookup"><span data-stu-id="ba97c-106">Member</span></span>|<span data-ttu-id="ba97c-107">描述</span><span class="sxs-lookup"><span data-stu-id="ba97c-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ba97c-108">主要</span><span class="sxs-lookup"><span data-stu-id="ba97c-108">Major</span></span>|<span data-ttu-id="ba97c-109">主要版本組建編號。</span><span class="sxs-lookup"><span data-stu-id="ba97c-109">Major version build number.</span></span>|  
|<span data-ttu-id="ba97c-110">Minor</span><span class="sxs-lookup"><span data-stu-id="ba97c-110">Minor</span></span>|<span data-ttu-id="ba97c-111">次要版本組建編號。</span><span class="sxs-lookup"><span data-stu-id="ba97c-111">Minor version build number.</span></span>|  
|<span data-ttu-id="ba97c-112">Sub</span><span class="sxs-lookup"><span data-stu-id="ba97c-112">Sub</span></span>|<span data-ttu-id="ba97c-113">子組建編號。</span><span class="sxs-lookup"><span data-stu-id="ba97c-113">Sub-build number.</span></span>|  
|<span data-ttu-id="ba97c-114">組建</span><span class="sxs-lookup"><span data-stu-id="ba97c-114">Build</span></span>|<span data-ttu-id="ba97c-115">組建編號。</span><span class="sxs-lookup"><span data-stu-id="ba97c-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ba97c-116">需求</span><span class="sxs-lookup"><span data-stu-id="ba97c-116">Requirements</span></span>  

 <span data-ttu-id="ba97c-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ba97c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba97c-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ba97c-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ba97c-119">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ba97c-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ba97c-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba97c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba97c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba97c-121">See also</span></span>

- [<span data-ttu-id="ba97c-122">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="ba97c-122">Metadata Structures</span></span>](metadata-structures.md)
