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
ms.openlocfilehash: ab74b02df959fe6e6457273e67ba3b82ae6a015c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436001"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="ffb62-102">IMetaDataDispenserEx::GetOption 方法</span><span class="sxs-lookup"><span data-stu-id="ffb62-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="ffb62-103">取得目前中繼資料範圍中指定之選項的值。</span><span class="sxs-lookup"><span data-stu-id="ffb62-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="ffb62-104">選項會控制如何處理對目前中繼資料範圍的呼叫。</span><span class="sxs-lookup"><span data-stu-id="ffb62-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffb62-105">語法</span><span class="sxs-lookup"><span data-stu-id="ffb62-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffb62-106">參數</span><span class="sxs-lookup"><span data-stu-id="ffb62-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="ffb62-107">在GUID 的指標，指定要抓取的選項。</span><span class="sxs-lookup"><span data-stu-id="ffb62-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="ffb62-108">如需支援的 Guid 清單，請參閱備註一節。</span><span class="sxs-lookup"><span data-stu-id="ffb62-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="ffb62-109">脫銷傳回之選項的值。</span><span class="sxs-lookup"><span data-stu-id="ffb62-109">[out] The value of the returned option.</span></span> <span data-ttu-id="ffb62-110">此值的類型將是指定之選項類型的 variant。</span><span class="sxs-lookup"><span data-stu-id="ffb62-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffb62-111">備註</span><span class="sxs-lookup"><span data-stu-id="ffb62-111">Remarks</span></span>  
 <span data-ttu-id="ffb62-112">下列清單顯示這個方法支援的 Guid。</span><span class="sxs-lookup"><span data-stu-id="ffb62-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="ffb62-113">如需說明，請參閱[IMetaDataDispenserEx：： SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ffb62-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="ffb62-114">如果 `optionId` 不在此清單中，這個方法會傳回 HRESULT `E_INVALIDARG`，表示參數不正確。</span><span class="sxs-lookup"><span data-stu-id="ffb62-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="ffb62-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="ffb62-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="ffb62-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="ffb62-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="ffb62-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="ffb62-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="ffb62-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="ffb62-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="ffb62-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="ffb62-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="ffb62-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="ffb62-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="ffb62-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="ffb62-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffb62-122">需求</span><span class="sxs-lookup"><span data-stu-id="ffb62-122">Requirements</span></span>  
 <span data-ttu-id="ffb62-123">**平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb62-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffb62-124">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ffb62-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ffb62-125">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ffb62-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ffb62-126">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffb62-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffb62-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffb62-127">See also</span></span>

- [<span data-ttu-id="ffb62-128">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="ffb62-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="ffb62-129">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="ffb62-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
