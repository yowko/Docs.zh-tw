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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f28facc8acb430de4aa255208a62c5fc61f12cd8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727660"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit 介面
提供方法來建立、 修改及儲存目前定義的範圍中的組件的相關中繼資料。 可以儲存在記憶體中的中繼資料，或儲存至磁碟。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ApplyEditAndContinue 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|使用指定所做的變更來更新目前的組件範圍`pImport`。|  
|[DefineCustomAttribute 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|建立自訂屬性的定義，具有指定之中繼資料簽章，附加至指定的物件，並取得該自訂屬性定義的語彙基元。|  
|[DefineEvent 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|建立事件的定義，具有指定之中繼資料簽章，並取得該事件定義語彙基元。|  
|[DefineField 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|建立欄位的定義，具有指定之中繼資料簽章，並取得該欄位定義的語彙基元。|  
|[DefineImportMember 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|建立目前的範圍之外的模組中定義，並取得該參考定義的語彙基元的型別成員的定義。|  
|[DefineImportType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|針對建立的定義，目前的範圍外的模組中定義，以及取得該參考定義的語彙基元型別的參考。|  
|[DefineMemberRef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|建立參考目前的範圍外的模組成員的定義，並取得該參考定義的語彙基元。|  
|[DefineMethod 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|使用指定的簽章中，建立方法的定義，並將權杖傳回給該方法的定義。|  
|[DefineMethodImpl 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|建立繼承自介面方法實作的定義，並將權杖傳回給該方法實作定義。|  
|[DefineModuleRef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|建立具有指定名稱的模組的中繼資料簽章。|  
|[DefineNestedType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|建立類型定義的中繼資料簽章，並傳回`mdTypeDef`另外定義的類型參考類型的成員來指定該類型的語彙基元`tdEncloser`。|  
|[DefineParam 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|使用指定的語彙基元所參考的方法指定的簽章建立的參數定義，並取得該參數定義的語彙基元。|  
|[DefinePermissionSet 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|建立使用權限集合與指定之中繼資料簽章的定義，並取得該權限集定義的語彙基元。|  
|[DefinePinvokeMap 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|設定指定的語彙基元所參考方法的 PInvoke 簽章的功能。|  
|[DefineProperty 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|建立具有指定的屬性定義指定的型別，如`get`和`set`方法存取子，並取得該屬性定義的語彙基元。|  
|[DefineSecurityAttributeSet 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|建立一組安全性權限，將附加到指定的語彙基元所參考的物件。|  
|[DefineTypeDef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|建立 common language runtime 型別中，型別定義，並取得該型別定義的中繼資料語彙基元。|  
|[DefineTypeRefByName 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|取得目前範圍以外的另一個模組中定義的型別中繼資料語彙基元。|  
|[DefineUserString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|取得指定的常值字串的中繼資料語彙基元。|  
|[DeleteClassLayout 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|終結指定的語彙基元所參考的類型的類別配置中繼資料簽章。|  
|[DeleteFieldMarshal 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|終結的 PInvoke 封送處理指定的語彙基元所參考之物件的中繼資料簽章。|  
|[DeletePinvokeMap 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|終結指定的語彙基元所參考物件的 PInvoke 對應中繼資料。|  
|[DeleteToken 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|從目前的中繼資料範圍中刪除指定的語彙基元。|  
|[GetSaveSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|目前範圍中取得的二進位的估計的大小，組件。|  
|[GetTokenFromSig 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|取得指定之中繼資料簽章的語彙基元。|  
|[GetTokenFromTypeSpec 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|取得具有指定之中繼資料簽章的類型中繼資料語彙基元。|  
|[Merge 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|將指定的匯入的範圍加入至要合併的範圍清單。|  
|[MergeEnd 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|合併到目前的範圍由一或多個先前的呼叫，以指定的所有中繼資料範圍`IMetaDataEmit::Merge`。|  
|[Save 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|將所有的中繼資料儲存在指定的位址檔案目前的範圍中。|  
|[SaveToMemory 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|將所有的中繼資料儲存在目前的範圍，以指定的記憶體區域。|  
|[SaveToStream 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|將所有的中繼資料儲存至指定目前範圍中`IStream`。|  
|[SetClassLayout 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|設定或更新先前呼叫所定義的類型的類別配置簽章`IMetaDataEmit::DefineTypeDef`。|  
|[SetCustomAttributeValue 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|設定或更新先前呼叫所定義的自訂屬性的值`IMetaDataEmit::DefineCustomAttribute`。|  
|[SetEventProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|設定或更新先前呼叫所定義的事件的指定的功能`IMetaDataEmit::DefineEvent`。|  
|[SetFieldMarshal 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|設定的 PInvoke 封送處理指定的語彙基元所參考的欄位、 return、 方法或方法參數的資訊。|  
|[SetFieldProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|設定或更新指定的欄位之語彙基元所參考之欄位的預設值。|  
|[SetFieldRVA 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|設定全域變數的值，指定語彙基元所參考之欄位的相對虛擬位址。|  
|[SetHandler 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|設定所指定參考的方法`IUnknown`指標當做權杖的重新對應的通知回呼。|  
|[SetMethodImplFlags 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|設定或更新指定的語彙基元所參考的繼承的方法實作的中繼資料簽章。|  
|[SetMethodProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|設定或更新功能，並儲存在指定相對虛擬位址，藉由先前呼叫所定義方法`IMetaDataEmit::DefineMethod`。|  
|[SetModuleProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|更新先前呼叫所定義的模組參考`IMetaDataEmit::DefineModuleRef`。|  
|[SetParamProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|設定或變更已由先前呼叫的方法參數的功能`IMetaDataEmit::DefineParam`。|  
|[SetParent 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|建立所指定的成員，由先前呼叫所定義`IMetaDataEmit::DefineMemberRef`，是由先前呼叫定義的成員，以指定的類型， `IMetaDataEmit::DefineTypeDef`。|  
|[SetPermissionSetProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|設定或更新的先前呼叫所定義的權限集合的中繼資料簽章功能`IMetaDataEmit::DefinePermissionSet`。|  
|[SetPinvokeMap 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|設定或變更功能的方法的 PInvoke 簽章，定義由先前呼叫`IMetaDataEmit::DefinePinvokeMap`。|  
|[SetPropertyProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|設定儲存在先前呼叫所定義之屬性的中繼資料的功能`IMetaDataEmit::DefineProperty`。|  
|[SetRVA 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|設定指定之方法的相對虛擬位址。|  
|[SetTypeDefProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|設定先前呼叫所定義之類型的功能`IMetaDataEmit::DefineTypeDef`。|  
|[TranslateSigWithScope 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|組件匯入目前的範圍，並取得新的中繼資料簽章為合併的範圍。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
