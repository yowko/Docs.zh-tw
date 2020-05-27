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
ms.openlocfilehash: 832adacac4a6df9ccf21578538a1c557150f3ba1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008777"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="fcc83-102">IMetaDataDispenserEx::GetOption 方法</span><span class="sxs-lookup"><span data-stu-id="fcc83-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="fcc83-103">取得目前中繼資料範圍中指定之選項的值。</span><span class="sxs-lookup"><span data-stu-id="fcc83-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="fcc83-104">選項會控制如何處理對目前中繼資料範圍的呼叫。</span><span class="sxs-lookup"><span data-stu-id="fcc83-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcc83-105">語法</span><span class="sxs-lookup"><span data-stu-id="fcc83-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcc83-106">參數</span><span class="sxs-lookup"><span data-stu-id="fcc83-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="fcc83-107">在GUID 的指標，指定要抓取的選項。</span><span class="sxs-lookup"><span data-stu-id="fcc83-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="fcc83-108">如需支援的 Guid 清單，請參閱備註一節。</span><span class="sxs-lookup"><span data-stu-id="fcc83-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="fcc83-109">脫銷傳回之選項的值。</span><span class="sxs-lookup"><span data-stu-id="fcc83-109">[out] The value of the returned option.</span></span> <span data-ttu-id="fcc83-110">此值的類型將是指定之選項類型的 variant。</span><span class="sxs-lookup"><span data-stu-id="fcc83-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcc83-111">備註</span><span class="sxs-lookup"><span data-stu-id="fcc83-111">Remarks</span></span>  
 <span data-ttu-id="fcc83-112">下列清單顯示這個方法支援的 Guid。</span><span class="sxs-lookup"><span data-stu-id="fcc83-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="fcc83-113">如需說明，請參閱[IMetaDataDispenserEx：： SetOption](imetadatadispenserex-setoption-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="fcc83-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="fcc83-114">如果 `optionId` 不在此清單中，這個方法會傳回 HRESULT `E_INVALIDARG` ，表示參數不正確。</span><span class="sxs-lookup"><span data-stu-id="fcc83-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="fcc83-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="fcc83-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="fcc83-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="fcc83-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="fcc83-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="fcc83-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="fcc83-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="fcc83-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="fcc83-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="fcc83-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="fcc83-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="fcc83-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="fcc83-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="fcc83-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcc83-122">需求</span><span class="sxs-lookup"><span data-stu-id="fcc83-122">Requirements</span></span>  
 <span data-ttu-id="fcc83-123">**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fcc83-123">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcc83-124">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="fcc83-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fcc83-125">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="fcc83-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fcc83-126">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcc83-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc83-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcc83-127">See also</span></span>

- [<span data-ttu-id="fcc83-128">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="fcc83-128">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="fcc83-129">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="fcc83-129">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
