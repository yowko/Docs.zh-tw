---
title: IMetaDataEmit::GetSaveSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
ms.openlocfilehash: 5cb202f5284c1c18545ec750b2fa0f04d4b0d2e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722059"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize 方法

取得元件的估計二進位大小及其在目前範圍中的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>參數  

 `fSave`  
 在 [CorSaveSize](corsavesize-enumeration.md) 列舉值，指定是否要取得精確或近似的大小。 只有三個值有效： cssAccurate、cssQuick 和 cssDiscardTransientCAs：  
  
- cssAccurate 會傳回確切的儲存大小，但需要較長的時間來計算。  
  
- cssQuick 會傳回大小，以填補安全，但需要較少的時間來計算。  
  
- cssDiscardTransientCAs 指出 `GetSaveSize` 它可能會擲回 discardable 的自訂屬性。  
  
 `pdwSaveSize`  
 擴展儲存檔案所需的大小指標。  
  
## <a name="remarks"></a>備註  

 `GetSaveSize` 以位元組為單位計算要儲存元件的空間，以及其在目前範圍中的所有中繼資料。  ([IMetaDataEmit：： SaveToStream](imetadataemit-savetostream-method.md) 方法的呼叫會發出此位元組數目。 )   
  
 如果呼叫端透過[IMetaDataEmit：： SetHandler](imetadataemit-sethandler-method.md)或[IMetaDataEmit：： Merge](imetadataemit-merge-method.md)) 來執行[IMapToken](imaptoken-interface.md)介面 (， `GetSaveSize` 將會對中繼資料執行兩次傳遞，以將其優化並加以壓縮。 否則，不會執行任何優化。  
  
 如果執行優化，則第一次傳遞只會排序元資料結構來調整匯入時間搜尋的效能。 此步驟通常會導致四處移動記錄，並且會影響工具保留的權杖以供日後參考。 不過，中繼資料不會在第二次通過之前通知這些權杖變更的呼叫端。 在第二個階段中，會執行各種優化，以減少中繼資料的整體大小，例如在 `mdTypeRef` `mdMemberRef` 參考至目前中繼資料範圍內所宣告的類型或成員時，將 (早期繫結) 和權杖優化。 在這個階段中，會發生另一輪 token 對應。 經過這次傳遞之後，中繼資料引擎會透過其 `IMapToken` 介面，通知任何已變更權杖值的呼叫端。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
