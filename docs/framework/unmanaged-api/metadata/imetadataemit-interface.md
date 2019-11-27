---
title: IMetaDataEmit 介面
ms.date: 03/30/2017
api_name:
- IMetaDataEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit
helpviewer_keywords:
- IMetaDataEmit interface [.NET Framework metadata]
ms.assetid: 3b48fd47-7397-4e2c-8bec-8157aa08978c
topic_type:
- apiref
ms.openlocfilehash: b4ae599a0e5cdb604fd9a610728671b39c67af31
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440894"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit 介面
提供方法，以在目前定義的範圍內建立、修改和儲存有關元件的中繼資料。 中繼資料可以儲存在記憶體中，或儲存至磁片。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ApplyEditAndContinue 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|使用在指定的 `pImport`中所做的變更，更新目前的元件範圍。|  
|[DefineCustomAttribute 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|使用指定的中繼資料簽章，建立自訂屬性的定義，以附加至指定的物件，並取得該自訂屬性定義的 token。|  
|[DefineEvent 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|使用指定的中繼資料簽章建立事件的定義，並取得該事件定義的 token。|  
|[DefineField 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|使用指定的中繼資料簽章建立欄位的定義，並取得該欄位定義的 token。|  
|[DefineImportMember 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|針對在目前範圍外的模組中定義的類型，建立其成員的定義，並取得該參考定義的 token。|  
|[DefineImportType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|針對在目前範圍外的模組中定義的類型，建立其參考的定義，並取得該參考定義的 token。|  
|[DefineMemberRef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|建立對目前範圍外之模組成員的參考定義，並取得該參考定義的 token。|  
|[DefineMethod 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|建立具有指定簽章之方法的定義，並將權杖傳回給該方法定義。|  
|[DefineMethodImpl 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|建立繼承自介面之方法的執行定義，並將權杖傳回給該方法執行定義。|  
|[DefineModuleRef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|建立具有指定名稱之模組的中繼資料簽章。|  
|[DefineNestedType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|建立類型定義的中繼資料簽章，並傳回該類型的 `mdTypeDef` token，另外指定定義的類型是 `tdEncloser`所參考之類型的成員。|  
|[DefineParam 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|針對指定之標記所參考的方法，使用指定的簽章建立參數定義，並取得該參數定義的 token。|  
|[DefinePermissionSet 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|使用指定的中繼資料簽章建立許可權集合的定義，並取得該許可權集合定義的 token。|  
|[DefinePinvokeMap 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|設定指定之標記所參考之方法的 PInvoke 簽章功能。|  
|[DefineProperty 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|使用指定的 `get` 和 `set` 方法存取子，為指定的類型建立屬性定義，並取得該屬性定義的 token。|  
|[DefineSecurityAttributeSet 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|建立一組安全性許可權，以附加至指定之標記所參考的物件。|  
|[DefineTypeDef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|建立 common language runtime 類型的類型定義，並取得該類型定義的元資料標記。|  
|[DefineTypeRefByName 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|取得在目前範圍以外的另一個模組中定義之類型的元資料標記。|  
|[DefineUserString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|取得指定之文字字串的元資料標記。|  
|[DeleteClassLayout 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|針對指定之標記所參考的類型，終結類別配置中繼資料簽章。|  
|[DeleteFieldMarshal 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|為指定之標記所參考的物件，終結 PInvoke 封送處理中繼資料簽章。|  
|[DeletePinvokeMap 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|為指定之標記所參考的物件，終結 PInvoke 對應中繼資料。|  
|[DeleteToken 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|從目前的中繼資料範圍中刪除指定的標記。|  
|[GetSaveSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|取得目前範圍中元件的估計二進位大小。|  
|[GetTokenFromSig 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|取得指定之中繼資料簽章的 token。|  
|[GetTokenFromTypeSpec 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|取得具有指定之中繼資料簽章之類型的元資料標記。|  
|[Merge 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|將指定的匯入範圍加入要合併的範圍清單。|  
|[MergeEnd 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|將一個或多個先前呼叫 `IMetaDataEmit::Merge`所指定的所有中繼資料範圍，合併到目前的範圍中。|  
|[Save 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|將目前範圍中的所有中繼資料，儲存至指定位址的檔案。|  
|[SaveToMemory 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|將目前範圍中的所有中繼資料儲存至指定的記憶體區域。|  
|[SaveToStream 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|將目前範圍中的所有中繼資料儲存至指定的 `IStream`。|  
|[SetClassLayout 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|設定或更新先前呼叫 `IMetaDataEmit::DefineTypeDef`所定義之類型的類別配置簽章。|  
|[SetCustomAttributeValue 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|設定或更新先前呼叫 `IMetaDataEmit::DefineCustomAttribute`所定義的自訂屬性值。|  
|[SetEventProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|設定或更新先前呼叫 `IMetaDataEmit::DefineEvent`所定義之事件的指定功能。|  
|[SetFieldMarshal 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|針對指定之標記所參考的欄位、方法傳回或方法參數，設定 PInvoke 封送處理資訊。|  
|[SetFieldProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|設定或更新指定欄位標記所參考之欄位的預設值。|  
|[SetFieldRVA 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|針對指定之標記所參考的欄位，設定其相對虛擬位址的全域變數值。|  
|[SetHandler 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|將指定之 `IUnknown` 指標所參考的方法設定為權杖重新對應的通知回呼。|  
|[SetMethodImplFlags 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|設定或更新指定之標記所參考的繼承方法實際引數資料簽章。|  
|[SetMethodProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|設定或更新由先前呼叫 `IMetaDataEmit::DefineMethod`所定義之方法中，儲存在指定之相對虛擬位址的功能。|  
|[SetModuleProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|更新先前呼叫 `IMetaDataEmit::DefineModuleRef`所定義之模組的參考。|  
|[SetParamProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|設定或變更先前呼叫所定義之方法參數的功能 `IMetaDataEmit::DefineParam`。|  
|[SetParent 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|建立指定的成員（如先前呼叫 `IMetaDataEmit::DefineMemberRef`所定義）是指定類型的成員，如先前呼叫 `IMetaDataEmit::DefineTypeDef`所定義。|  
|[SetPermissionSetProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|設定或更新先前呼叫 `IMetaDataEmit::DefinePermissionSet`所定義之許可權集合的中繼資料簽章的功能。|  
|[SetPinvokeMap 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|設定或變更方法之 PInvoke 簽章的功能，如先前的 `IMetaDataEmit::DefinePinvokeMap`呼叫所定義。|  
|[SetPropertyProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|針對先前呼叫 `IMetaDataEmit::DefineProperty`所定義的屬性，設定儲存在中繼資料中的功能。|  
|[SetRVA 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|設定指定方法的相對虛擬位址。|  
|[SetTypeDefProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|設定先前呼叫 `IMetaDataEmit::DefineTypeDef`所定義之類型的功能。|  
|[TranslateSigWithScope 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|將元件匯入到目前的範圍，並為合併的範圍取得新的中繼資料簽章。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
