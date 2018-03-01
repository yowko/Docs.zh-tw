---
title: "IMetaDataEmit::MergeEnd 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 265fc007b5817e8dffd5846738a7a0003bbddf9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd 方法
合併到目前範圍的一個或多個先前呼叫所指定的所有中繼資料範圍[imetadataemit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會採用任何參數。  
  
## <a name="remarks"></a>備註  
 這個常式會觸發實際的合併中繼資料，所有的匯入前的呼叫中指定的範圍`IMetaDataEmit::Merge`，到目前的輸出範圍。  
  
 下列的特殊情況適用於合併式：  
  
-   模組版本識別項 (MVID) 永遠不會匯入，因為它是唯一的中繼資料匯入範圍中。  
  
-   會覆不寫任何現有的整個模組的屬性。  
  
     如果模組屬性已設定為目前的範圍，會匯不入任何模組的屬性。 不過，如果模組屬性尚未設定在目前範圍中，它們會匯入一次，當第一次遇到。 如果這些模組內容發生一次，它們是重複的項目。 如果 （MVID 除外） 的所有模組屬性的值進行比較並發現沒有重複項目，則會引發錯誤。  
  
-   類型定義 (`TypeDef`)，沒有重複項目會合併到目前的範圍。 `TypeDef`物件會檢查是否有重複項目針對每個*完整物件名稱* + *GUID* + *版本號碼*。 如果沒有符合項目名稱或 GUID，且任何其他兩個項目不同，則會引發錯誤。 否則，如果所有的三個項目相符，`MergeEnd`未執行快速檢查，以確保項目確實是重複項目; 如果沒有，則會引發錯誤。 這項快速檢查會尋找：  
  
    -   相同成員宣告中的相同順序發生。 成員標示為`mdPrivateScope`(請參閱[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列舉型別) 中這項檢查; 不包含特殊合併。  
  
    -   相同的類別配置。  
  
     這表示`TypeDef`物件必須一律完整且一致地定義每個中繼資料範圍內宣告中，如果其成員的實作 （類別） 會橫跨多個編譯單位中，假設為完整定義每個範圍中存在且不增量至每個範圍。 比方說，如果參數名稱與合約相關，他們必須發出相同的方式納入每個範圍中。如果不相關，他們應該不發出至中繼資料。  
  
     例外狀況是，`TypeDef`物件可以有標示為增量成員`mdPrivateScope`。 在發生時，這些項目，`MergeEnd`以累加方式將它們加入至目前的範圍，而不考慮重複項目。 由於編譯器了解私人範圍，編譯器必須負責強制執行規則。  
  
-   相對虛擬位址 (Rva) 不會匯入或合併。編譯器預期會重新發出這項資訊。  
  
-   自訂屬性合併只能附加至的項目會合併。 比方說，第一次遇到類別時，會合併類別相關聯的自訂屬性。 如果自訂屬性相關聯`TypeDef`或`MemberDef`專屬於編譯單位 （例如成員編譯的時間戳記），它們不會合併會決定移除或更新中繼資料，這類編譯器。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
