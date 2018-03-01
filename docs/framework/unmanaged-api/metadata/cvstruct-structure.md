---
title: "CVStruct 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e0c9087b180b39185fbf66235b515b9742e69ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cvstruct-structure"></a><span data-ttu-id="3aa37-102">CVStruct 結構</span><span class="sxs-lookup"><span data-stu-id="3aa37-102">CVStruct Structure</span></span>
<span data-ttu-id="3aa37-103">包含在安裝模組或複合映像時，所使用的資訊。</span><span class="sxs-lookup"><span data-stu-id="3aa37-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aa37-104">語法</span><span class="sxs-lookup"><span data-stu-id="3aa37-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="3aa37-105">成員</span><span class="sxs-lookup"><span data-stu-id="3aa37-105">Members</span></span>  
  
|<span data-ttu-id="3aa37-106">成員</span><span class="sxs-lookup"><span data-stu-id="3aa37-106">Member</span></span>|<span data-ttu-id="3aa37-107">描述</span><span class="sxs-lookup"><span data-stu-id="3aa37-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3aa37-108">主要</span><span class="sxs-lookup"><span data-stu-id="3aa37-108">Major</span></span>|<span data-ttu-id="3aa37-109">主要版本的組建編號。</span><span class="sxs-lookup"><span data-stu-id="3aa37-109">Major version build number.</span></span>|  
|<span data-ttu-id="3aa37-110">次要</span><span class="sxs-lookup"><span data-stu-id="3aa37-110">Minor</span></span>|<span data-ttu-id="3aa37-111">次要版本組建編號。</span><span class="sxs-lookup"><span data-stu-id="3aa37-111">Minor version build number.</span></span>|  
|<span data-ttu-id="3aa37-112">Sub</span><span class="sxs-lookup"><span data-stu-id="3aa37-112">Sub</span></span>|<span data-ttu-id="3aa37-113">子組建編號。</span><span class="sxs-lookup"><span data-stu-id="3aa37-113">Sub-build number.</span></span>|  
|<span data-ttu-id="3aa37-114">組建</span><span class="sxs-lookup"><span data-stu-id="3aa37-114">Build</span></span>|<span data-ttu-id="3aa37-115">組建編號。</span><span class="sxs-lookup"><span data-stu-id="3aa37-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3aa37-116">需求</span><span class="sxs-lookup"><span data-stu-id="3aa37-116">Requirements</span></span>  
 <span data-ttu-id="3aa37-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3aa37-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aa37-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3aa37-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3aa37-119">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3aa37-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3aa37-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aa37-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aa37-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="3aa37-121">See Also</span></span>  
 [<span data-ttu-id="3aa37-122">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="3aa37-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
