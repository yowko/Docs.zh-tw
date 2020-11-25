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
ms.openlocfilehash: 60d321c1a87a5da433437c9d4587fa9f8947acf4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713375"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="3400b-102">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="3400b-102">IMetaDataDispenserEx Interface</span></span>

<span data-ttu-id="3400b-103">擴充 [IMetaDataDispenser 介面](imetadatadispenser-interface.md) 介面，以提供控制中繼資料 api 在目前中繼資料範圍上運作方式的功能。</span><span class="sxs-lookup"><span data-stu-id="3400b-103">Extends the [IMetaDataDispenser Interface](imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3400b-104">方法</span><span class="sxs-lookup"><span data-stu-id="3400b-104">Methods</span></span>  
  
|<span data-ttu-id="3400b-105">方法</span><span class="sxs-lookup"><span data-stu-id="3400b-105">Method</span></span>|<span data-ttu-id="3400b-106">描述</span><span class="sxs-lookup"><span data-stu-id="3400b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3400b-107">FindAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="3400b-107">FindAssembly Method</span></span>](imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="3400b-108">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="3400b-108">This method is not implemented.</span></span> <span data-ttu-id="3400b-109">如果呼叫，則會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="3400b-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="3400b-110">FindAssemblyModule 方法</span><span class="sxs-lookup"><span data-stu-id="3400b-110">FindAssemblyModule Method</span></span>](imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="3400b-111">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="3400b-111">This method is not implemented.</span></span> <span data-ttu-id="3400b-112">如果呼叫，則會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="3400b-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="3400b-113">GetCORSystemDirectory 方法</span><span class="sxs-lookup"><span data-stu-id="3400b-113">GetCORSystemDirectory Method</span></span>](imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="3400b-114">取得保存目前 common language runtime (CLR) 的目錄。</span><span class="sxs-lookup"><span data-stu-id="3400b-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="3400b-115">只有跨進程偵錯工具才能使用此方法。</span><span class="sxs-lookup"><span data-stu-id="3400b-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="3400b-116">如果從另一個元件呼叫，則會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="3400b-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="3400b-117">GetOption 方法</span><span class="sxs-lookup"><span data-stu-id="3400b-117">GetOption Method</span></span>](imetadatadispenserex-getoption-method.md)|<span data-ttu-id="3400b-118">取得目前中繼資料範圍之指定選項的值。</span><span class="sxs-lookup"><span data-stu-id="3400b-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="3400b-119">選項會控制如何處理目前中繼資料範圍的呼叫。</span><span class="sxs-lookup"><span data-stu-id="3400b-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="3400b-120">OpenScopeOnITypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="3400b-120">OpenScopeOnITypeInfo Method</span></span>](imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="3400b-121">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="3400b-121">This method is not implemented.</span></span> <span data-ttu-id="3400b-122">如果呼叫，則會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="3400b-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="3400b-123">SetOption 方法</span><span class="sxs-lookup"><span data-stu-id="3400b-123">SetOption Method</span></span>](imetadatadispenserex-setoption-method.md)|<span data-ttu-id="3400b-124">將指定的選項設定為目前中繼資料範圍的指定值。</span><span class="sxs-lookup"><span data-stu-id="3400b-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="3400b-125">選項會控制如何處理目前中繼資料範圍的呼叫。</span><span class="sxs-lookup"><span data-stu-id="3400b-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3400b-126">需求</span><span class="sxs-lookup"><span data-stu-id="3400b-126">Requirements</span></span>  

 <span data-ttu-id="3400b-127">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3400b-127">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3400b-128">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3400b-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3400b-129">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="3400b-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3400b-130">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3400b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3400b-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3400b-131">See also</span></span>

- [<span data-ttu-id="3400b-132">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="3400b-132">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="3400b-133">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="3400b-133">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="3400b-134">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3400b-134">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3400b-135">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="3400b-135">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
