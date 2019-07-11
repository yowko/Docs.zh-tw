---
title: IMetaDataDispenserEx::SetOption 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.SetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::SetOption
helpviewer_keywords:
- IMetaDataDispenserEx::SetOption method [.NET Framework metadata]
- SetOption method [.NET Framework metadata]
ms.assetid: 9f1c7ccd-7fb2-41d8-aa00-24b823376527
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6916e6344fe5c112b216ca753c372fa73a4d5af5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777710"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption 方法
將指定的選項，設定目前的中繼資料範圍的指定值。 此選項會控制如何處理目前的中繼資料範圍的呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `optionId`  
 [in]指定要設定選項的 GUID 指標。  
  
 `pValue`  
 [in]若要使用設定選項值。 此值的型別必須是指定的選項類型的 variant。  
  
## <a name="remarks"></a>備註  
 下表列出可用的 Guid，`optionId`參數可以指向和對應的有效值為`pValue`參數。  
  
|GUID|描述|`pValue` 參數|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|控制哪些項目會檢查有重複的項目。 每次呼叫[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)方法，以建立新的項目，您可以要求要檢查的項目是否已存在於目前範圍的方法。 例如，您可以檢查是否存在`mdMethodDef`項目; 在此情況下，當您呼叫[imetadataemit:: Definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)，它會檢查方法已不存在目前的範圍中。 這項檢查會使用金鑰可唯一識別指定的方法： 父型別、 名稱和簽章。|必須是類型 UI4 的 variant，而且必須包含值的組合[CorCheckDuplicatesFor](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md)列舉型別。|  
|MetaDataRefToDefCheck|控制哪些參考的項目會轉換為定義。 根據預設，中繼資料引擎會最佳化的程式碼，藉由將參考的項目轉換為其定義中，如果參考的項目實際上定義於目前的範圍。|必須是類型 UI4 的 variant，而且必須包含值的組合[CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md)列舉型別。|  
|MetaDataNotificationForTokenMovement|權杖會重新對應的中繼資料合併期間所發生的控制項產生回呼。 使用[imetadataemit:: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)方法，以建立您[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)介面。|必須是類型 UI4 的 variant，而且必須包含值的組合[CorNotificationForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md)列舉型別。|  
|MetaDataSetENC|控制行為的編輯後繼續 (ENC)。 只有一個模式的行為可以設定一次。|必須是類型 UI4 的 variant，而且必須包含值[CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md)列舉型別。 值不是位元遮罩。|  
|MetaDataErrorIfEmitOutOfOrder|哪些發出-的次序不對錯誤產生回呼的控制項。 發出中繼資料的順序並不嚴重的;不過，如果您發出中繼資料的中繼資料引擎偏好的順序，中繼資料而言較為精簡，因此可更有效率地搜尋。 使用`IMetaDataEmit::SetHandler`方法，以建立您[IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)介面。|必須是類型 UI4 的 variant，而且必須包含值的組合[CorErrorIfEmitOutOfOrder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md)列舉型別。|  
|MetaDataImportOption|控制哪些類型的 ENC 期間已刪除的項目所擷取列舉值。|必須是類型 UI4 的 variant，而且必須包含值的組合[CorImportOptions 列舉](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md)列舉型別。|  
|MetaDataThreadSafetyOptions|控制是否中繼資料引擎取得讀取器/寫入器鎖定，藉此確保執行緒安全性。 根據預設，引擎會假設，存取是單一執行緒的呼叫端，因此不會取得鎖定。 用戶端會負責維護適當的執行緒同步處理時使用的中繼資料 API。|必須是類型 UI4 的 variant，而且必須包含值[CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md)列舉型別。 值不是位元遮罩。|  
|MetaDataGenerateTCEAdapters|控制項類型程式庫匯入工具是否應該產生緊密結合的事件 (TCE) 配接器，適用於 COM 連接點容器。|必須是 BOOL 類型的 variant。 如果`pValue`設為`true`，類型程式庫匯入工具會產生 TCE 配接器。|  
|MetaDataTypeLibImportNamespace|指定正在匯入的類型程式庫的非預設命名空間。|必須是 null 值或 BSTR 類型的 variant。 如果`pValue`為 null 的值，目前的命名空間設為 null，否則目前的命名空間會設為會保留在 variant 的 BSTR 類型的字串。|  
|MetaDataLinkerOptions|控制連結器是否應該產生組件或.NET Framework 模組檔案。|必須是類型 UI4 的 variant，而且必須包含值的組合[CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md)列舉型別。|  
|MetaDataRuntimeVersion|指定針對此映像所建立的 common language runtime 版本。 版本會儲存為字串，例如 「 v1.0.3705 」。|必須是 null 值、 VT_EMPTY 值或 BSTR 類型的 variant。 如果`pValue`是 null，執行階段版本設為 null。 如果`pValue`為 VT_EMPTY，版本設定為預設值，所繪製的中繼資料的程式碼執行所在的 Mscorwks.dll 版本中。 否則，執行階段版本設為會保留在 variant 的 BSTR 類型的字串。|  
|MetaDataMergerOptions|指定合併中繼資料的選項。|必須是類型 UI4 的 variant，而且必須包含值的組合`MergeFlags`CorHdr.h 檔案中所述的列舉。|  
|MetaDataPreserveLocalRefs|停用最佳化成定義的本機參考。|必須包含值的組合[CorLocalRefPreservation](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md)列舉型別。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataDispenserEx 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
