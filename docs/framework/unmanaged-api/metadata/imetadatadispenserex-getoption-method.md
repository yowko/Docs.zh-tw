---
title: IMetaDataDispenserEx::GetOption 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe9bc9aea4ceb0f5b5c03416f43894b482c3294e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136626"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="71216-102">IMetaDataDispenserEx::GetOption 方法</span><span class="sxs-lookup"><span data-stu-id="71216-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="71216-103">取得目前的中繼資料範圍的指定選項的值。</span><span class="sxs-lookup"><span data-stu-id="71216-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="71216-104">此選項會控制如何處理目前的中繼資料範圍的呼叫。</span><span class="sxs-lookup"><span data-stu-id="71216-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71216-105">語法</span><span class="sxs-lookup"><span data-stu-id="71216-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71216-106">參數</span><span class="sxs-lookup"><span data-stu-id="71216-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="71216-107">[in]指定要擷取的選項為 guid 的指標。</span><span class="sxs-lookup"><span data-stu-id="71216-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="71216-108">請參閱支援的 Guid 清單 < 備註 > 一節。</span><span class="sxs-lookup"><span data-stu-id="71216-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="71216-109">[out]傳回選項的值。</span><span class="sxs-lookup"><span data-stu-id="71216-109">[out] The value of the returned option.</span></span> <span data-ttu-id="71216-110">此值的型別會指定的選項類型的 variant。</span><span class="sxs-lookup"><span data-stu-id="71216-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71216-111">備註</span><span class="sxs-lookup"><span data-stu-id="71216-111">Remarks</span></span>  
 <span data-ttu-id="71216-112">下列清單顯示支援此方法的 Guid。</span><span class="sxs-lookup"><span data-stu-id="71216-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="71216-113">如需說明，請參閱[imetadatadispenserex:: Setoption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="71216-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="71216-114">如果`optionId`是不在此清單中，這個方法會傳回 HRESULT `E_INVALIDARG`，指出不正確的參數。</span><span class="sxs-lookup"><span data-stu-id="71216-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="71216-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="71216-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="71216-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="71216-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="71216-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="71216-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="71216-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="71216-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="71216-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="71216-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="71216-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="71216-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="71216-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="71216-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71216-122">需求</span><span class="sxs-lookup"><span data-stu-id="71216-122">Requirements</span></span>  
 <span data-ttu-id="71216-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="71216-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71216-124">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="71216-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="71216-125">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="71216-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="71216-126">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71216-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71216-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71216-127">See also</span></span>

- [<span data-ttu-id="71216-128">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="71216-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="71216-129">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="71216-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
