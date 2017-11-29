---
title: "IMetaDataDispenserEx 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx
helpviewer_keywords: IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5ecb4e94c0deed3ed62b2d2eb8b0309ca092abf8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="a0ada-102">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="a0ada-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="a0ada-103">擴充[IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)介面，以提供控制中繼資料 Api 目前的中繼資料範圍上的操作方式的能力。</span><span class="sxs-lookup"><span data-stu-id="a0ada-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0ada-104">方法</span><span class="sxs-lookup"><span data-stu-id="a0ada-104">Methods</span></span>  
  
|<span data-ttu-id="a0ada-105">方法</span><span class="sxs-lookup"><span data-stu-id="a0ada-105">Method</span></span>|<span data-ttu-id="a0ada-106">說明</span><span class="sxs-lookup"><span data-stu-id="a0ada-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0ada-107">FindAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="a0ada-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="a0ada-108">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="a0ada-108">This method is not implemented.</span></span> <span data-ttu-id="a0ada-109">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="a0ada-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="a0ada-110">FindAssemblyModule 方法</span><span class="sxs-lookup"><span data-stu-id="a0ada-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="a0ada-111">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="a0ada-111">This method is not implemented.</span></span> <span data-ttu-id="a0ada-112">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="a0ada-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="a0ada-113">GetCORSystemDirectory 方法</span><span class="sxs-lookup"><span data-stu-id="a0ada-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="a0ada-114">取得儲存目前的 common language runtime (CLR) 的目錄。</span><span class="sxs-lookup"><span data-stu-id="a0ada-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="a0ada-115">這個方法是僅支援使用由跨處理序偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="a0ada-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="a0ada-116">如果已從另一個元件呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="a0ada-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="a0ada-117">GetOption 方法</span><span class="sxs-lookup"><span data-stu-id="a0ada-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="a0ada-118">取得目前中繼資料範圍的指定選項的值。</span><span class="sxs-lookup"><span data-stu-id="a0ada-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="a0ada-119">此選項會控制如何處理目前的中繼資料範圍的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a0ada-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="a0ada-120">OpenScopeOnITypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="a0ada-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="a0ada-121">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="a0ada-121">This method is not implemented.</span></span> <span data-ttu-id="a0ada-122">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="a0ada-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="a0ada-123">SetOption 方法</span><span class="sxs-lookup"><span data-stu-id="a0ada-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="a0ada-124">將指定的選項設定為目前中繼資料範圍的指定值。</span><span class="sxs-lookup"><span data-stu-id="a0ada-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="a0ada-125">此選項會控制如何處理目前的中繼資料範圍的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a0ada-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0ada-126">需求</span><span class="sxs-lookup"><span data-stu-id="a0ada-126">Requirements</span></span>  
 <span data-ttu-id="a0ada-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0ada-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0ada-128">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a0ada-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0ada-129">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a0ada-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0ada-130">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0ada-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0ada-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0ada-131">See Also</span></span>  
 [<span data-ttu-id="a0ada-132">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="a0ada-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="a0ada-133">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="a0ada-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="a0ada-134">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a0ada-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a0ada-135">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a0ada-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
