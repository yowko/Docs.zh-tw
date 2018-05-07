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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d9a65f76aed00e2b848f8603f1fee4d6acc91f99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize 方法
在目前範圍中取得的二進位的估計的大小，組件和它的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fSave`  
 [in]值為[CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md)列舉，指定是否要取得的精確或大約大小。 只有三個值都有效： cssAccurate，cssQuick，和 cssDiscardTransientCAs:  
  
-   cssAccurate 傳回精確的儲存大小，但所花費的時間來計算。  
  
-   cssQuick 傳回基於安全考量，填補的大小，但花較少的時間計算。  
  
-   cssDiscardTransientCAs 告訴`GetSaveSize`，它可以擲回了可捨棄的自訂屬性。  
  
 `pdwSaveSize`  
 [out]指標，才能儲存檔案的大小。  
  
## <a name="remarks"></a>備註  
 `GetSaveSize` 計算所需的空間，以位元組為單位，將組件和其所有中繼資料儲存在目前的範圍。 (呼叫[imetadataemit:: Savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)方法會發出此位元組數目。)  
  
 如果呼叫端實作[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)介面 (透過[imetadataemit:: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)或[imetadataemit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md))，`GetSaveSize`將會執行兩種途徑透過以最佳化，並壓縮的中繼資料。 否則，不會執行最佳化。  
  
 如果執行最佳化，則第一個階段只是排序要微調效能的匯入時搜尋的中繼資料結構。 這個步驟通常都會具有副作用，保留供日後參考工具的語彙基元都會失效記錄四處移動。 中繼資料並不會通知這些語彙基元的變更，直到呼叫之後的第二個階段，不過。 在第二個階段中，各種最佳化所執行的要減少整體的中繼資料，例如離開 （早期繫結） 的最佳化大小`mdTypeRef`和`mdMemberRef`權杖型別或成員宣告的參考時目前的中繼資料範圍。 在這個階段中，就會發生另一回合的語彙基元對應。 中繼資料引擎之後此階段，透過通知呼叫端，其`IMapToken`介面，任何變更的語彙基元值。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
