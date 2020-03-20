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
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption 方法
獲取當前中繼資料作用域的指定選項的值。 該選項控制如何處理對當前中繼資料作用域的調用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `optionId`  
 [在]指向 GUID 的指標，用於指定要檢索的選項。 有關支援的 GUID 的清單，請參閱備註部分。  
  
 `pValue`  
 [出]返回的選項的值。 此值的類型將是指定選項類型的變體。  
  
## <a name="remarks"></a>備註  
 下面的清單顯示了此方法支援的 GUID。 有關說明，請參閱[IMetaDataDispenserEx：：SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)方法。 如果`optionId`不在此清單中，此方法將返回 HRESULT `E_INVALIDARG`，指示不正確的參數。  
  
- 中繼資料檢查重複項  
  
- 中繼資料參考檢查  
  
- 中繼資料通知權杖移動  
  
- 元資料集  
  
- 中繼資料錯誤，如果已發出命令  
  
- 中繼資料生成配接器  
  
- 元資料連結器選項  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataDispenserEx 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
