---
title: "IMetaDataDispenser 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser
helpviewer_keywords: IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5a0464f2fb7b81d98fcbb4b04bc465cf57b1b0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="f991f-102">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="f991f-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="f991f-103">提供建立新的中繼資料範圍，或開啟現有的方法。</span><span class="sxs-lookup"><span data-stu-id="f991f-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f991f-104">方法</span><span class="sxs-lookup"><span data-stu-id="f991f-104">Methods</span></span>  
  
|<span data-ttu-id="f991f-105">方法</span><span class="sxs-lookup"><span data-stu-id="f991f-105">Method</span></span>|<span data-ttu-id="f991f-106">說明</span><span class="sxs-lookup"><span data-stu-id="f991f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f991f-107">DefineScope 方法</span><span class="sxs-lookup"><span data-stu-id="f991f-107">DefineScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|<span data-ttu-id="f991f-108">您可以在其中建立新的中繼資料的記憶體中建立新的區域。</span><span class="sxs-lookup"><span data-stu-id="f991f-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="f991f-109">OpenScope 方法</span><span class="sxs-lookup"><span data-stu-id="f991f-109">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|<span data-ttu-id="f991f-110">開啟現有磁碟上的檔案，並將它的中繼資料對應到記憶體中。</span><span class="sxs-lookup"><span data-stu-id="f991f-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="f991f-111">OpenScopeOnMemory 方法</span><span class="sxs-lookup"><span data-stu-id="f991f-111">OpenScopeOnMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="f991f-112">開啟包含現有的中繼資料的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="f991f-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="f991f-113">也就是說，這個方法會開啟指定的現有資料會被視為中繼資料的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="f991f-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f991f-114">需求</span><span class="sxs-lookup"><span data-stu-id="f991f-114">Requirements</span></span>  
 <span data-ttu-id="f991f-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f991f-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f991f-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f991f-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f991f-117">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f991f-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f991f-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f991f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f991f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f991f-119">See Also</span></span>  
 [<span data-ttu-id="f991f-120">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="f991f-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="f991f-121">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="f991f-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
