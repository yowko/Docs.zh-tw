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
ms.openlocfilehash: d9279808e4ad15b693d06ac8a99dd33a609e5a8f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169048"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize 方法
目前範圍中取得的二進位的估計的大小，組件和它的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>參數  
 `fSave`  
 [in]值為[CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md)列舉，指定是否要取得精確或近似大小。 只有三個值都有效： cssAccurate，cssQuick，和 cssDiscardTransientCAs:  
  
-   cssAccurate 傳回的確切的儲存大小，但所花費的時間來計算。  
  
-   cssQuick 傳回基於安全考量，填補的大小，但需要較少的時間來計算。  
  
-   cssDiscardTransientCAs 告訴`GetSaveSize`，它可以擲出可捨棄的自訂屬性。  
  
 `pdwSaveSize`  
 [out]指標，才能儲存檔案的大小。  
  
## <a name="remarks"></a>備註  
 `GetSaveSize` 計算所需的空間，以位元組為單位，將組件和其所有中繼資料儲存在目前的範圍。 (呼叫[imetadataemit:: Savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)方法會發出此位元組數目。)  
  
 如果呼叫者會實作[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)介面 (透過[imetadataemit:: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)或是[imetadataemit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md))，`GetSaveSize`會執行兩個階段若要最佳化，並將它壓縮之中繼資料。 否則，不會執行最佳化。  
  
 如果執行最佳化，則第一次傳遞只是排序的中繼資料結構，以微調效能的匯入時的搜尋。 此步驟通常會導致移動，具有副作用，保留供日後參考工具的權杖都會失效的記錄。 中繼資料並不會通知呼叫端的這些語彙基元的變更，直到之後的第二個階段，不過。 在第二個階段中，各種最佳化所執行的目的為了避免，請在中繼資料，例如最佳化離開 （早期繫結） 的整體大小`mdTypeRef`和`mdMemberRef`語彙基元型別或成員中所宣告的參考時目前的中繼資料範圍。 在此階段中，就會發生另一回合的語彙基元對應。 在此階段之後, 的中繼資料引擎會通知呼叫端，透過其`IMapToken`介面，任何變更語彙基元值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
