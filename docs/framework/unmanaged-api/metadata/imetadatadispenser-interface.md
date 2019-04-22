---
title: IMetaDataDispenser 介面
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dda284fc86f0a82472c59d6bab08fd4a87364723
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225972"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="3a06b-102">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="3a06b-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="3a06b-103">提供方法來建立新的中繼資料範圍，或開啟現有實驗。</span><span class="sxs-lookup"><span data-stu-id="3a06b-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a06b-104">方法</span><span class="sxs-lookup"><span data-stu-id="3a06b-104">Methods</span></span>  
  
|<span data-ttu-id="3a06b-105">方法</span><span class="sxs-lookup"><span data-stu-id="3a06b-105">Method</span></span>|<span data-ttu-id="3a06b-106">描述</span><span class="sxs-lookup"><span data-stu-id="3a06b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a06b-107">DefineScope 方法</span><span class="sxs-lookup"><span data-stu-id="3a06b-107">DefineScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|<span data-ttu-id="3a06b-108">您可以在其中建立新的中繼資料的記憶體中建立新的區域。</span><span class="sxs-lookup"><span data-stu-id="3a06b-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="3a06b-109">OpenScope 方法</span><span class="sxs-lookup"><span data-stu-id="3a06b-109">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|<span data-ttu-id="3a06b-110">開啟現有磁碟上的檔案，並將它的中繼資料對應到記憶體。</span><span class="sxs-lookup"><span data-stu-id="3a06b-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="3a06b-111">OpenScopeOnMemory 方法</span><span class="sxs-lookup"><span data-stu-id="3a06b-111">OpenScopeOnMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="3a06b-112">開啟包含現有的中繼資料的記憶體中的區域。</span><span class="sxs-lookup"><span data-stu-id="3a06b-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="3a06b-113">也就是說，這個方法會開啟指定的現有資料會被視為中繼資料的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="3a06b-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a06b-114">需求</span><span class="sxs-lookup"><span data-stu-id="3a06b-114">Requirements</span></span>  
 <span data-ttu-id="3a06b-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a06b-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a06b-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3a06b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a06b-117">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3a06b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a06b-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a06b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a06b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a06b-119">See also</span></span>

- [<span data-ttu-id="3a06b-120">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="3a06b-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="3a06b-121">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="3a06b-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
