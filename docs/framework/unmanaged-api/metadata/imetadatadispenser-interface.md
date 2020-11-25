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
ms.openlocfilehash: c798aeba46adf91a8c13f8143c00f02173a0bb52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726102"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="db360-102">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="db360-102">IMetaDataDispenser Interface</span></span>

<span data-ttu-id="db360-103">提供方法來建立新的中繼資料範圍，或開啟現有的範圍。</span><span class="sxs-lookup"><span data-stu-id="db360-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db360-104">方法</span><span class="sxs-lookup"><span data-stu-id="db360-104">Methods</span></span>  
  
|<span data-ttu-id="db360-105">方法</span><span class="sxs-lookup"><span data-stu-id="db360-105">Method</span></span>|<span data-ttu-id="db360-106">描述</span><span class="sxs-lookup"><span data-stu-id="db360-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db360-107">DefineScope 方法</span><span class="sxs-lookup"><span data-stu-id="db360-107">DefineScope Method</span></span>](imetadatadispenser-definescope-method.md)|<span data-ttu-id="db360-108">在記憶體中建立新的區域，您可以在其中建立新的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="db360-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="db360-109">OpenScope 方法</span><span class="sxs-lookup"><span data-stu-id="db360-109">OpenScope Method</span></span>](imetadatadispenser-openscope-method.md)|<span data-ttu-id="db360-110">開啟現有的磁片上的檔案，並將其中繼資料對應到記憶體。</span><span class="sxs-lookup"><span data-stu-id="db360-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="db360-111">OpenScopeOnMemory 方法</span><span class="sxs-lookup"><span data-stu-id="db360-111">OpenScopeOnMemory Method</span></span>](imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="db360-112">開啟包含現有中繼資料的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="db360-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="db360-113">也就是說，這個方法會開啟指定的記憶體區域，其中現有的資料會被視為中繼資料。</span><span class="sxs-lookup"><span data-stu-id="db360-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db360-114">需求</span><span class="sxs-lookup"><span data-stu-id="db360-114">Requirements</span></span>  

 <span data-ttu-id="db360-115">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db360-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db360-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="db360-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db360-117">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="db360-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db360-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db360-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db360-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db360-119">See also</span></span>

- [<span data-ttu-id="db360-120">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="db360-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="db360-121">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="db360-121">Metadata Interfaces</span></span>](metadata-interfaces.md)
