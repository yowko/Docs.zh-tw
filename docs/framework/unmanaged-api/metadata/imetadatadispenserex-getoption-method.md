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
ms.openlocfilehash: a117fcdf2ba9d37fb5483cc85fb575e5d3476794
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption 方法
取得目前中繼資料範圍的指定選項的值。 此選項會控制如何處理目前的中繼資料範圍的呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `optionId`  
 [in]指定要擷取的選項為 guid 的指標。 請參閱 < 備註 > 一節清單的支援的 Guid。  
  
 `pValue`  
 [out]傳回選項的值。 此值的型別會指定的選項類型的 variant。  
  
## <a name="remarks"></a>備註  
 下列清單顯示支援這個方法的 Guid。 如需說明，請參閱[imetadatadispenserex:: Setoption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)方法。 如果`optionId`是不在此清單中，這個方法會傳回 HRESULT `E_INVALIDARG`，指出不正確的參數。  
  
-   MetaDataCheckDuplicatesFor  
  
-   MetaDataRefToDefCheck  
  
-   MetaDataNotificationForTokenMovement  
  
-   MetaDataSetENC  
  
-   MetaDataErrorIfEmitOutOfOrder  
  
-   MetaDataGenerateTCEAdapters  
  
-   MetaDataLinkerOptions  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataDispenserEx 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
