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
ms.openlocfilehash: 816e2f2dc7d4d00f74f67720ee45d7b3483e57fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177723"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="8fc02-102">IMetaDataDispenserEx::GetOption 方法</span><span class="sxs-lookup"><span data-stu-id="8fc02-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="8fc02-103">獲取當前中繼資料作用域的指定選項的值。</span><span class="sxs-lookup"><span data-stu-id="8fc02-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="8fc02-104">該選項控制如何處理對當前中繼資料作用域的調用。</span><span class="sxs-lookup"><span data-stu-id="8fc02-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc02-105">語法</span><span class="sxs-lookup"><span data-stu-id="8fc02-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fc02-106">參數</span><span class="sxs-lookup"><span data-stu-id="8fc02-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="8fc02-107">[在]指向 GUID 的指標，用於指定要檢索的選項。</span><span class="sxs-lookup"><span data-stu-id="8fc02-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="8fc02-108">有關支援的 GUID 的清單，請參閱備註部分。</span><span class="sxs-lookup"><span data-stu-id="8fc02-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="8fc02-109">[出]返回的選項的值。</span><span class="sxs-lookup"><span data-stu-id="8fc02-109">[out] The value of the returned option.</span></span> <span data-ttu-id="8fc02-110">此值的類型將是指定選項類型的變體。</span><span class="sxs-lookup"><span data-stu-id="8fc02-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fc02-111">備註</span><span class="sxs-lookup"><span data-stu-id="8fc02-111">Remarks</span></span>  
 <span data-ttu-id="8fc02-112">下面的清單顯示了此方法支援的 GUID。</span><span class="sxs-lookup"><span data-stu-id="8fc02-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="8fc02-113">有關說明，請參閱[IMetaDataDispenserEx：：SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="8fc02-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="8fc02-114">如果`optionId`不在此清單中，此方法將返回 HRESULT `E_INVALIDARG`，指示不正確的參數。</span><span class="sxs-lookup"><span data-stu-id="8fc02-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="8fc02-115">中繼資料檢查重複項</span><span class="sxs-lookup"><span data-stu-id="8fc02-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="8fc02-116">中繼資料參考檢查</span><span class="sxs-lookup"><span data-stu-id="8fc02-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="8fc02-117">中繼資料通知權杖移動</span><span class="sxs-lookup"><span data-stu-id="8fc02-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="8fc02-118">元資料集</span><span class="sxs-lookup"><span data-stu-id="8fc02-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="8fc02-119">中繼資料錯誤，如果已發出命令</span><span class="sxs-lookup"><span data-stu-id="8fc02-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="8fc02-120">中繼資料生成配接器</span><span class="sxs-lookup"><span data-stu-id="8fc02-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="8fc02-121">元資料連結器選項</span><span class="sxs-lookup"><span data-stu-id="8fc02-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc02-122">需求</span><span class="sxs-lookup"><span data-stu-id="8fc02-122">Requirements</span></span>  
 <span data-ttu-id="8fc02-123">**平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc02-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fc02-124">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="8fc02-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8fc02-125">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8fc02-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8fc02-126">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fc02-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc02-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fc02-127">See also</span></span>

- [<span data-ttu-id="8fc02-128">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="8fc02-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="8fc02-129">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="8fc02-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
