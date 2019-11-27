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
ms.openlocfilehash: bc30f9fb120db92ccfc1e7dd0560b3fe18c54b29
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432737"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption 方法
針對目前的中繼資料範圍，將指定的選項設定為指定的值。 選項會控制如何處理對目前中繼資料範圍的呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `optionId`  
 在GUID 的指標，指定要設定的選項。  
  
 `pValue`  
 在要用來設定選項的值。 此值的類型必須是指定之選項類型的變體。  
  
## <a name="remarks"></a>備註  
 下表列出 `optionId` 參數可指向的可用 Guid，以及 `pValue` 參數的對應有效值。  
  
|GUID|描述|`pValue` 參數|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|控制要檢查哪些專案的複本是否重複。 每次呼叫建立新專案的[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)方法時，您都可以要求方法檢查該專案是否已存在於目前的範圍中。 例如，您可以檢查 `mdMethodDef` 專案是否存在;在此情況下，當您呼叫[IMetaDataEmit：:D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)時，它會檢查方法是否尚未存在於目前的範圍中。 這項檢查會使用可唯一識別指定方法的索引鍵：父類型、名稱和簽章。|必須是 UI4 類型的變數，而且必須包含[CorCheckDuplicatesFor](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md)列舉值的組合。|  
|MetaDataRefToDefCheck|控制要將哪些參考的專案轉換成定義。 根據預設，如果參考的專案實際上是在目前的範圍中定義，中繼資料引擎就會將參考的專案轉換為其定義，以優化程式碼。|必須是 UI4 類型的變數，而且必須包含[CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md)列舉值的組合。|  
|MetaDataNotificationForTokenMovement|控制在中繼資料合併期間發生哪些標記重新對應產生回呼。 使用[IMetaDataEmit：： SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)方法來建立您的[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)介面。|必須是 UI4 類型的變數，而且必須包含[CorNotificationForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md)列舉值的組合。|  
|MetaDataSetENC|控制 [編輯後繼續] （ENC）的行為。 一次只能設定一種行為模式。|必須是 UI4 類型的變數，而且必須包含[CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md)列舉的值。 此值不是位元遮罩。|  
|MetaDataErrorIfEmitOutOfOrder|控制哪些發出的順序錯誤產生回呼。 以順序發出中繼資料並不嚴重;不過，如果您以中繼資料引擎偏好的順序發出中繼資料，中繼資料會更精簡，因此可以更有效率地搜尋。 使用 `IMetaDataEmit::SetHandler` 方法來建立您的[IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)介面。|必須是 UI4 類型的變數，而且必須包含[CorErrorIfEmitOutOfOrder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md)列舉值的組合。|  
|MetaDataImportOption|控制由列舉值抓取在 ENC 期間刪除的專案類型。|必須是 UI4 類型的變數，而且必須包含[CorImportOptions 列舉](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md)列舉的值組合。|  
|MetaDataThreadSafetyOptions|控制中繼資料引擎是否取得讀取器/寫入器鎖定，以確保執行緒安全性。 根據預設，引擎會假設呼叫端的存取是單一執行緒，因此不會取得任何鎖定。 當使用中繼資料 API 時，用戶端會負責維護適當的執行緒同步處理。|必須是 UI4 類型的變數，而且必須包含[CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md)列舉的值。 此值不是位元遮罩。|  
|MetaDataGenerateTCEAdapters|控制型別程式庫匯入工具是否應為 COM 連接點容器產生緊密結合的事件（TCE）介面卡。|必須是 BOOL 類型的 variant。 如果 `pValue` 設定為 `true`，類型程式庫匯入工具會產生 TCE 介面卡。|  
|MetaDataTypeLibImportNamespace|指定要匯入之類型程式庫的非預設命名空間。|必須是 null 值或 BSTR 類型的 variant。 如果 `pValue` 為 null 值，則目前的命名空間會設定為 null;否則，目前的命名空間會設定為變數的 BSTR 類型中保留的字串。|  
|MetaDataLinkerOptions|控制連結器是否應該產生元件或 .NET Framework 模組檔案。|必須是 UI4 類型的變數，而且必須包含[CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md)列舉值的組合。|  
|MetaDataRuntimeVersion|指定用來建立此映射的 common language runtime 版本。 版本會儲存為字串，例如 "v v1.0.3705"。|必須是 null 值、VT_EMPTY 值或 BSTR 類型的 variant。 如果 `pValue` 為 null，則執行階段版本會設定為 null。 如果 VT_EMPTY `pValue`，則會將版本設定為預設值，而這是從中繼資料程式碼執行所在的 Mscorwks.dll 版本中繪製而來。 否則，執行階段版本會設定為變數的 BSTR 類型中保留的字串。|  
|MetaDataMergerOptions|指定用於合併中繼資料的選項。|必須是 UI4 類型的變數，而且必須包含 Corhdr.h 中所述的 `MergeFlags` 列舉值的組合。|  
|MetaDataPreserveLocalRefs|停用將本機參考優化為定義。|必須包含[CorLocalRefPreservation](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md)列舉的值組合。|  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IMetaDataDispenserEx 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
