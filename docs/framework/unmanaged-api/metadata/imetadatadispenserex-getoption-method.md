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
ms.openlocfilehash: 0ceadf42ac49fd3fc89c78a6a26b2f529afeeaf0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700557"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="923d1-102">IMetaDataDispenserEx::GetOption 方法</span><span class="sxs-lookup"><span data-stu-id="923d1-102">IMetaDataDispenserEx::GetOption Method</span></span>

<span data-ttu-id="923d1-103">取得目前中繼資料範圍之指定選項的值。</span><span class="sxs-lookup"><span data-stu-id="923d1-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="923d1-104">選項會控制如何處理目前中繼資料範圍的呼叫。</span><span class="sxs-lookup"><span data-stu-id="923d1-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="923d1-105">語法</span><span class="sxs-lookup"><span data-stu-id="923d1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="923d1-106">參數</span><span class="sxs-lookup"><span data-stu-id="923d1-106">Parameters</span></span>  

 `optionId`  
 <span data-ttu-id="923d1-107">在GUID 的指標，指定要取出的選項。</span><span class="sxs-lookup"><span data-stu-id="923d1-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="923d1-108">請參閱「備註」一節，以取得支援的 Guid 清單。</span><span class="sxs-lookup"><span data-stu-id="923d1-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="923d1-109">擴展傳回之選項的值。</span><span class="sxs-lookup"><span data-stu-id="923d1-109">[out] The value of the returned option.</span></span> <span data-ttu-id="923d1-110">此值的類型將會是所指定選項類型的變數。</span><span class="sxs-lookup"><span data-stu-id="923d1-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="923d1-111">備註</span><span class="sxs-lookup"><span data-stu-id="923d1-111">Remarks</span></span>  

 <span data-ttu-id="923d1-112">下列清單顯示此方法支援的 Guid。</span><span class="sxs-lookup"><span data-stu-id="923d1-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="923d1-113">如需相關說明，請參閱 [IMetaDataDispenserEx：： SetOption](imetadatadispenserex-setoption-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="923d1-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="923d1-114">如果 `optionId` 不在此清單中，這個方法會傳回 HRESULT `E_INVALIDARG` ，指出不正確的參數。</span><span class="sxs-lookup"><span data-stu-id="923d1-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="923d1-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="923d1-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="923d1-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="923d1-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="923d1-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="923d1-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="923d1-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="923d1-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="923d1-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="923d1-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="923d1-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="923d1-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="923d1-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="923d1-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="923d1-122">需求</span><span class="sxs-lookup"><span data-stu-id="923d1-122">Requirements</span></span>  

 <span data-ttu-id="923d1-123">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="923d1-123">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="923d1-124">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="923d1-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="923d1-125">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="923d1-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="923d1-126">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="923d1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="923d1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="923d1-127">See also</span></span>

- [<span data-ttu-id="923d1-128">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="923d1-128">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="923d1-129">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="923d1-129">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
