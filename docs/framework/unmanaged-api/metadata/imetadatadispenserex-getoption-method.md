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
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption 方法

取得目前中繼資料範圍之指定選項的值。 選項會控制如何處理目前中繼資料範圍的呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>參數  

 `optionId`  
 在GUID 的指標，指定要取出的選項。 請參閱「備註」一節，以取得支援的 Guid 清單。  
  
 `pValue`  
 擴展傳回之選項的值。 此值的類型將會是所指定選項類型的變數。  
  
## <a name="remarks"></a>備註  

 下列清單顯示此方法支援的 Guid。 如需相關說明，請參閱 [IMetaDataDispenserEx：： SetOption](imetadatadispenserex-setoption-method.md) 方法。 如果 `optionId` 不在此清單中，這個方法會傳回 HRESULT `E_INVALIDARG` ，指出不正確的參數。  
  
- MetaDataCheckDuplicatesFor  
  
- MetaDataRefToDefCheck  
  
- MetaDataNotificationForTokenMovement  
  
- MetaDataSetENC  
  
- MetaDataErrorIfEmitOutOfOrder  
  
- MetaDataGenerateTCEAdapters  
  
- MetaDataLinkerOptions  
  
## <a name="requirements"></a>需求  

 **平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataDispenserEx 介面](imetadatadispenserex-interface.md)
- [IMetaDataDispenser 介面](imetadatadispenser-interface.md)
