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
ms.openlocfilehash: f8e85a670d04e5825653864484b7ccd9ce747949
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175898"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption 方法
將指定選項設置為當前中繼資料作用域的給定值。 該選項控制如何處理對當前中繼資料作用域的調用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `optionId`  
 [在]指向 GUID 的指標，用於指定要設置的選項。  
  
 `pValue`  
 [在]用於設置選項的值。 此值的類型必須是指定選項類型的變體。  
  
## <a name="remarks"></a>備註  
 下表列出了`optionId`參數可以指向的可用 GUID 以及`pValue`參數的相應有效值。  
  
|GUID|描述|`pValue`參數|  
|----------|-----------------|------------------------|  
|中繼資料檢查重複項|控制檢查哪些項的重複項。 每次調用創建新專案的[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)方法時，都可以要求該方法檢查該項是否已存在於當前作用域中。 例如，您可以檢查`mdMethodDef`是否存在專案;例如，可以檢查是否存在專案。在這種情況下，當您調用[IMetaDataEmit：:DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)時，它將檢查該方法是否不存在在當前作用域中。 此檢查使用唯一標識給定方法的鍵：父類型、名稱和簽名。|必須是類型 UI4 的變體，並且必須包含[CorCheck 複製項的值的組合。For](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md)枚舉。|  
|中繼資料參考檢查|引用項的控制項將轉換為定義。 預設情況下，如果引用的項實際上是在當前作用域中定義的，中繼資料引擎將通過將引用的項轉換為其定義來優化代碼。|必須是類型 UI4 的變體，並且必須包含[CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md)枚舉的值的組合。|  
|中繼資料通知權杖移動|控制在中繼資料合併期間發生的權杖重映射生成回檔。 使用[IMetaDataEmit：：SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)方法建立[IMapToken 介面](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)。|必須是類型 UI4 的變體，並且必須包含[Cor通知ForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md)枚舉的值的組合。|  
|元資料集|控制編輯和繼續 （ENC） 的行為。 一次只能設置一種行為模式。|必須是類型 UI4 的變體，並且必須包含[CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md)枚舉的值。 該值不是位元遮罩。|  
|中繼資料錯誤，如果已發出命令|控制發出訂單外錯誤生成回檔。 按順序發出中繼資料並非致命;但是，如果按中繼資料引擎青睞的順序發出中繼資料，則中繼資料將更加緊湊，因此可以更有效地搜索中繼資料。 使用`IMetaDataEmit::SetHandler`方法建立[IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)介面。|必須是類型 UI4 的變體，並且必須包含[CorErrorIfEmitOutOrder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md)枚舉的值的組合。|  
|中繼資料導入選項|控制枚舉器檢索在 ENC 期間刪除的哪些類型的項。|必須是類型 UI4 的變體，並且必須包含[CorImportOptions 枚舉](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md)枚舉的值的組合。|  
|中繼資料執行緒安全選項|控制中繼資料引擎是否獲取讀取器/寫入器鎖，從而確保執行緒安全。 預設情況下，引擎假定訪問由調用方單線程進行，因此不會獲取鎖。 用戶端負責在使用中繼資料 API 時保持正確的執行緒同步。|必須是類型 UI4 的變體，並且必須包含[CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md)枚舉的值。 該值不是位元遮罩。|  
|中繼資料生成配接器|控制型別程式庫導入器是否應為 COM 連接點容器生成緊密耦合的事件 （TCE） 配接器。|必須是 BOOL 類型的變體。 如果`pValue`設置為`true`，型別程式庫導入器將生成 TCE 配接器。|  
|MetaDataTypeLib導入命名空間|為要導入的型別程式庫指定非預設命名空間。|必須為空值或 BSTR 類型的變體。 如果`pValue`為空值，則當前命名空間設置為 null;如果為 null。"如果為空"，則為 null。否則，當前命名空間將設置為在變體的 BSTR 類型中持有的字串。|  
|元資料連結器選項|控制連結器是生成程式集還是 .NET 框架模組檔。|必須是類型 UI4 的變體，並且必須包含[CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md)枚舉的值的組合。|  
|中繼資料執行階段版本|指定生成此映射的通用語言運行時的版本。 版本存儲為字串，如"v1.0.3705"。|必須為空值、VT_EMPTY值或 BSTR 類型的變體。 如果`pValue`為 null，則執行階段版本設置為 null。 如果`pValue`VT_EMPTY，則版本設置為預設值，該值從運行中繼資料代碼的 Mscorwks.dll 版本中提取。 否則，執行階段版本將設置為在變體的 BSTR 類型中持有的字串。|  
|中繼資料合併選項|指定合併中繼資料的選項。|必須是類型 UI4 的變體，並且必須包含枚舉值`MergeFlags`的組合，這在 CorHdr.h 檔中描述。|  
|MetaData 保留本地引用|禁用將本地引用優化到定義中。|必須包含[CorLocalRef 保存](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md)枚舉的值的組合。|  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataDispenserEx 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
