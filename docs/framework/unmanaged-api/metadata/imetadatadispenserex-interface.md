---
title: IMetaDataDispenserEx 介面
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: 96f0c0c254ce255581ac2937c805096918ab29e8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008049"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="9a6a7-102">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="9a6a7-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="9a6a7-103">擴充[IMetaDataDispenser 介面](imetadatadispenser-interface.md)介面，以提供可控制中繼資料 api 如何在目前中繼資料範圍上運作的功能。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-103">Extends the [IMetaDataDispenser Interface](imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a6a7-104">方法</span><span class="sxs-lookup"><span data-stu-id="9a6a7-104">Methods</span></span>  
  
|<span data-ttu-id="9a6a7-105">方法</span><span class="sxs-lookup"><span data-stu-id="9a6a7-105">Method</span></span>|<span data-ttu-id="9a6a7-106">描述</span><span class="sxs-lookup"><span data-stu-id="9a6a7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9a6a7-107">FindAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="9a6a7-107">FindAssembly Method</span></span>](imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="9a6a7-108">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-108">This method is not implemented.</span></span> <span data-ttu-id="9a6a7-109">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="9a6a7-110">FindAssemblyModule 方法</span><span class="sxs-lookup"><span data-stu-id="9a6a7-110">FindAssemblyModule Method</span></span>](imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="9a6a7-111">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-111">This method is not implemented.</span></span> <span data-ttu-id="9a6a7-112">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="9a6a7-113">GetCORSystemDirectory 方法</span><span class="sxs-lookup"><span data-stu-id="9a6a7-113">GetCORSystemDirectory Method</span></span>](imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="9a6a7-114">取得保存目前 common language runtime （CLR）的目錄。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="9a6a7-115">這個方法僅支援跨進程偵錯工具使用。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="9a6a7-116">如果從另一個元件呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="9a6a7-117">GetOption 方法</span><span class="sxs-lookup"><span data-stu-id="9a6a7-117">GetOption Method</span></span>](imetadatadispenserex-getoption-method.md)|<span data-ttu-id="9a6a7-118">取得目前中繼資料範圍中指定之選項的值。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="9a6a7-119">選項會控制如何處理對目前中繼資料範圍的呼叫。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="9a6a7-120">OpenScopeOnITypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="9a6a7-120">OpenScopeOnITypeInfo Method</span></span>](imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="9a6a7-121">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-121">This method is not implemented.</span></span> <span data-ttu-id="9a6a7-122">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="9a6a7-123">SetOption 方法</span><span class="sxs-lookup"><span data-stu-id="9a6a7-123">SetOption Method</span></span>](imetadatadispenserex-setoption-method.md)|<span data-ttu-id="9a6a7-124">針對目前的中繼資料範圍，將指定的選項設定為指定的值。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="9a6a7-125">選項會控制如何處理對目前中繼資料範圍的呼叫。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a6a7-126">需求</span><span class="sxs-lookup"><span data-stu-id="9a6a7-126">Requirements</span></span>  
 <span data-ttu-id="9a6a7-127">**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-127">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a6a7-128">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="9a6a7-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a6a7-129">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="9a6a7-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a6a7-130">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a6a7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a6a7-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a6a7-131">See also</span></span>

- [<span data-ttu-id="9a6a7-132">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="9a6a7-132">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="9a6a7-133">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="9a6a7-133">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="9a6a7-134">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="9a6a7-134">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9a6a7-135">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="9a6a7-135">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
