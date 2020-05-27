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
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption 方法
取得目前中繼資料範圍中指定之選項的值。 選項會控制如何處理對目前中繼資料範圍的呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `optionId`  
 在GUID 的指標，指定要抓取的選項。 如需支援的 Guid 清單，請參閱備註一節。  
  
 `pValue`  
 脫銷傳回之選項的值。 此值的類型將是指定之選項類型的 variant。  
  
## <a name="remarks"></a>備註  
 下列清單顯示這個方法支援的 Guid。 如需說明，請參閱[IMetaDataDispenserEx：： SetOption](imetadatadispenserex-setoption-method.md)方法。 如果 `optionId` 不在此清單中，這個方法會傳回 HRESULT `E_INVALIDARG` ，表示參數不正確。  
  
- MetaDataCheckDuplicatesFor  
  
- MetaDataRefToDefCheck  
  
- MetaDataNotificationForTokenMovement  
  
- MetaDataSetENC  
  
- MetaDataErrorIfEmitOutOfOrder  
  
- MetaDataGenerateTCEAdapters  
  
- MetaDataLinkerOptions  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataDispenserEx 介面](imetadatadispenserex-interface.md)
- [IMetaDataDispenser 介面](imetadatadispenser-interface.md)
