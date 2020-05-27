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
ms.openlocfilehash: 22c0a317777a12294ba7a90f7af1ceeca3ad0a47
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009258"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize 方法
取得元件及其中繼資料在目前範圍中的估計二進位大小。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>參數  
 `fSave`  
 在[CorSaveSize](corsavesize-enumeration.md)列舉的值，指定是否要取得精確或近似的大小。 只有三個有效的值： cssAccurate、cssQuick 和 cssDiscardTransientCAs：  
  
- cssAccurate 會傳回完全相同的儲存大小，但需要較長的時間來計算。  
  
- cssQuick 會傳回大小，以填補安全性，但花費較少的時間來計算。  
  
- cssDiscardTransientCAs `GetSaveSize` 會告訴它可以捨棄可捨棄的自訂屬性。  
  
 `pdwSaveSize`  
 脫銷儲存檔案所需大小的指標。  
  
## <a name="remarks"></a>備註  
 `GetSaveSize`計算所需的空間（以位元組為單位），以將元件及其所有中繼資料儲存在目前的範圍中。 （呼叫[IMetaDataEmit：： SaveToStream](imetadataemit-savetostream-method.md)方法會發出此位元組數目）。  
  
 如果呼叫端實[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)介面（透過[IMetaDataEmit：： SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)或[IMetaDataEmit：： Merge](imetadataemit-merge-method.md)）， `GetSaveSize` 將會對中繼資料執行兩次傳遞，以將它優化並加以壓縮。 否則，不會執行任何優化。  
  
 如果執行優化，第一次傳遞只會將元資料結構排序，以微調匯入時間搜尋的效能。 此步驟通常會導致移動記錄，而副作用是由工具所保留以供日後參考的權杖會失效。 不過，中繼資料不會通知呼叫者這些權杖變更，直到第二次傳遞為止。 在第二個階段中，會執行各種優化，以減少中繼資料的整體大小，例如， `mdTypeRef` `mdMemberRef` 當參考指向目前中繼資料範圍內所宣告的類型或成員時，將其優化（早期繫結）和標記。 在此階段中，會發生另一個標記對應的迴圈。 在此階段之後，中繼資料引擎會透過其介面，通知呼叫端 `IMapToken` 任何已變更的 token 值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
