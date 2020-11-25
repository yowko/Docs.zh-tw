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
ms.openlocfilehash: 4216658eb562c5c57b75c3c257cd8e53a7a34221
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700583"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption 方法

將指定的選項設定為目前中繼資料範圍的指定值。 選項會控制如何處理目前中繼資料範圍的呼叫。  
  
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
 在用來設定選項的值。 此值的型別必須是指定之選項型別的變數。  
  
## <a name="remarks"></a>備註  

 下表列出參數可指向的可用 Guid `optionId` ，以及參數的對應有效值 `pValue` 。  
  
|GUID|描述|`pValue` 參數|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|控制要檢查哪些專案有重複的專案。 每次呼叫建立新專案的 [IMetaDataEmit](imetadataemit-interface.md) 方法時，您都可以要求方法檢查項目是否已存在於目前的範圍中。 例如，您可以檢查項目是否存在， `mdMethodDef` 在此案例中，當您呼叫 [IMetaDataEmit：:D efinemethod](imetadataemit-definemethod-method.md)時，它會檢查方法是否不存在於目前的範圍中。 這項檢查會使用可唯一識別指定方法的金鑰：父類型、名稱和簽章。|必須是 UI4 類型的變體，而且必須包含 [CorCheckDuplicatesFor](corcheckduplicatesfor-enumeration.md) 列舉值的組合。|  
|MetaDataRefToDefCheck|控制哪些參考的專案會轉換成定義。 根據預設，如果參考的專案實際上是在目前的範圍中定義，中繼資料引擎會將參考的專案轉換成其定義，以將程式碼優化。|必須是 UI4 類型的變體，而且必須包含 [CorRefToDefCheck](correftodefcheck-enumeration.md) 列舉值的組合。|  
|MetaDataNotificationForTokenMovement|控制中繼資料合併期間發生的標記重新對應會產生回呼。 使用 [IMetaDataEmit：： SetHandler](imetadataemit-sethandler-method.md) 方法來建立 [IMapToken](imaptoken-interface.md) 介面。|必須是 UI4 類型的變體，而且必須包含 [CorNotificationForTokenMovement](cornotificationfortokenmovement-enumeration.md) 列舉值的組合。|  
|MetaDataSetENC|控制編輯後繼續 (ENC) 的行為。 一次只能設定一個行為模式。|必須是 UI4 類型的變體，而且必須包含 [CorSetENC](corsetenc-enumeration.md) 列舉的值。 值不是位元遮罩。|  
|MetaDataErrorIfEmitOutOfOrder|控制產生回呼的發出順序錯誤。 發出未按順序的中繼資料不是嚴重的;但是，如果您以中繼資料引擎所偏好的順序發出中繼資料，中繼資料會更精簡，因此可以更有效率地搜尋。 使用 `IMetaDataEmit::SetHandler` 方法來建立您的 [IMetaDataError](imetadataerror-interface.md) 介面。|必須是 UI4 類型的變體，而且必須包含 [CorErrorIfEmitOutOfOrder](corerrorifemitoutoforder-enumeration.md) 列舉值的組合。|  
|MetaDataImportOption|控制列舉值在 ENC 期間所刪除的專案類型。|必須是 UI4 類型的變體，而且必須包含 [CorImportOptions 列舉](corimportoptions-enumeration.md) 列舉值的組合。|  
|MetaDataThreadSafetyOptions|控制中繼資料引擎是否取得讀取器/寫入器鎖定，進而確保執行緒安全。 根據預設，引擎會假設呼叫者會以單一執行緒的方式進行存取，因此不會取得鎖定。 使用中繼資料 API 時，用戶端會負責維護適當的執行緒同步處理。|必須是 UI4 類型的變體，而且必須包含 [CorThreadSafetyOptions](corthreadsafetyoptions-enumeration.md) 列舉的值。 值不是位元遮罩。|  
|MetaDataGenerateTCEAdapters|控制類型程式庫匯入工具是否應該產生緊密結合的事件 (適用于 COM 連接點容器的 TCE) 介面卡。|必須是 BOOL 類型的變數。 如果 `pValue` 設定為 `true` ，則類型程式庫匯入工具會產生 TCE 介面卡。|  
|MetaDataTypeLibImportNamespace|為正在匯入的類型程式庫指定非預設的命名空間。|必須是 null 值或類型 BSTR 的 variant。 如果 `pValue` 是 null 值，則目前的命名空間會設定為 null，否則，目前的命名空間會設定為變數的 BSTR 類型中所保留的字串。|  
|MetaDataLinkerOptions|控制連結器是否應該產生元件或 .NET Framework 模組檔案。|必須是 UI4 類型的變體，而且必須包含 [CorLinkerOptions](corlinkeroptions-enumeration.md) 列舉值的組合。|  
|MetaDataRuntimeVersion|指定用來建立此映射的 common language runtime 版本。 版本會儲存為字串，例如 "v v1.0.3705"。|必須是 null 值、VT_EMPTY 值或 BSTR 類型的 variant。 如果 `pValue` 是 null，則執行階段版本會設定為 null。 如果 `pValue` VT_EMPTY，則會將版本設定為預設值，而此值是從中繼資料程式碼執行所在的 Mscorwks.dll 版本中繪製。 否則，執行階段版本會設定為保留在 variant 之 BSTR 類型中的字串。|  
|MetaDataMergerOptions|指定用於合併中繼資料的選項。|必須是 UI4 類型的變體，而且必須包含列舉值的組合 `MergeFlags` ，如 corhdr.h .h 檔案中所述。|  
|MetaDataPreserveLocalRefs|停用將本機參考優化成定義。|必須包含 [CorLocalRefPreservation](corlocalrefpreservation-enumeration.md) 列舉值的組合。|  
  
## <a name="requirements"></a>需求  

 **平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataDispenserEx 介面](imetadatadispenserex-interface.md)
- [IMetaDataDispenser 介面](imetadatadispenser-interface.md)
