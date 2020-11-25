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
ms.openlocfilehash: f5495c170abf3e991a6e28016687f8ae77f0b423
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722020"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit 介面

提供方法，以建立、修改和儲存目前定義範圍中元件的相關中繼資料。 中繼資料可以儲存在記憶體中或儲存至磁片。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ApplyEditAndContinue 方法](imetadataemit-applyeditandcontinue-method.md)|使用在指定的中所做的變更，來更新目前的元件範圍 `pImport` 。|  
|[DefineCustomAttribute 方法](imetadataemit-definecustomattribute-method.md)|使用指定的中繼資料簽章來建立自訂屬性的定義，以附加至指定的物件，並取得該自訂屬性定義的標記。|  
|[DefineEvent 方法](imetadataemit-defineevent-method.md)|使用指定的中繼資料簽章建立事件的定義，並取得該事件定義的權杖。|  
|[DefineField 方法](imetadataemit-definefield-method.md)|使用指定的中繼資料簽章建立欄位的定義，並取得該欄位定義的標記。|  
|[DefineImportMember 方法](imetadataemit-defineimportmember-method.md)|針對在目前範圍之外的模組中定義之類型的成員建立定義，並取得該參考定義的標記。|  
|[DefineImportType 方法](imetadataemit-defineimporttype-method.md)|針對在目前範圍之外之模組中定義的類型，建立參考的定義，並取得該參考定義的標記。|  
|[DefineMemberRef 方法](imetadataemit-definememberref-method.md)|針對目前範圍之外的模組成員，建立參考的定義，並取得該參考定義的標記。|  
|[DefineMethod 方法](imetadataemit-definemethod-method.md)|使用指定的簽章來建立方法的定義，並將標記傳回至該方法定義。|  
|[DefineMethodImpl 方法](imetadataemit-definemethodimpl-method.md)|建立用來執行繼承自介面之方法的定義，並將標記傳回至該方法執行定義。|  
|[DefineModuleRef 方法](imetadataemit-definemoduleref-method.md)|使用指定的名稱，建立模組的中繼資料簽章。|  
|[DefineNestedType 方法](imetadataemit-definenestedtype-method.md)|建立類型定義的中繼資料簽章，並傳回 `mdTypeDef` 該類型的標記，另外指定定義的類型是所參考型別的成員 `tdEncloser` 。|  
|[DefineParam 方法](imetadataemit-defineparam-method.md)|針對指定之標記所參考的方法，使用指定的簽章建立參數定義，並取得該參數定義的標記。|  
|[DefinePermissionSet 方法](imetadataemit-definepermissionset-method.md)|使用指定的中繼資料簽章，建立許可權集合的定義，並取得該許可權集定義的標記。|  
|[DefinePinvokeMap 方法](imetadataemit-definepinvokemap-method.md)|設定指定之標記所參考之方法的 PInvoke 簽章功能。|  
|[DefineProperty 方法](imetadataemit-defineproperty-method.md)|使用指定的和方法存取子，針對指定的型別建立屬性定義， `get` `set` 並取得該屬性定義的標記。|  
|[DefineSecurityAttributeSet 方法](imetadataemit-definesecurityattributeset-method.md)|建立一組安全性許可權，以附加至指定標記所參考的物件。|  
|[DefineTypeDef 方法](imetadataemit-definetypedef-method.md)|建立通用語言執行時間類型的類型定義，並取得該類型定義的元資料標記。|  
|[DefineTypeRefByName 方法](imetadataemit-definetyperefbyname-method.md)|取得類型的元資料標記，該類型定義于目前範圍之外的另一個模組中。|  
|[DefineUserString 方法](imetadataemit-defineuserstring-method.md)|取得指定之常值字串的元資料標記。|  
|[DeleteClassLayout 方法](imetadataemit-deleteclasslayout-method.md)|終結指定標記所參考之型別的類別配置中繼資料簽章。|  
|[DeleteFieldMarshal 方法](imetadataemit-deletefieldmarshal-method.md)|終結 PInvoke 封送處理指定標記所參考物件的中繼資料簽章。|  
|[DeletePinvokeMap 方法](imetadataemit-deletepinvokemap-method.md)|終結指定標記所參考物件的 PInvoke 對應中繼資料。|  
|[DeleteToken 方法](imetadataemit-deletetoken-method.md)|從目前的中繼資料範圍中刪除指定的標記。|  
|[GetSaveSize 方法](imetadataemit-getsavesize-method.md)|取得目前範圍中元件的估計二進位大小。|  
|[GetTokenFromSig 方法](imetadataemit-gettokenfromsig-method.md)|取得指定之中繼資料簽章的標記。|  
|[GetTokenFromTypeSpec 方法](imetadataemit-gettokenfromtypespec-method.md)|取得具有指定中繼資料簽章之類型的元資料標記。|  
|[Merge 方法](imetadataemit-merge-method.md)|將指定的匯入範圍加入要合併的範圍清單。|  
|[MergeEnd 方法](imetadataemit-mergeend-method.md)|將一或多個先前呼叫所指定的所有中繼資料範圍合併到目前的範圍中 `IMetaDataEmit::Merge` 。|  
|[Save 方法](imetadataemit-save-method.md)|將目前範圍中的所有中繼資料儲存至檔案的指定位址。|  
|[SaveToMemory 方法](imetadataemit-savetomemory-method.md)|將目前範圍中的所有中繼資料儲存至指定的記憶體區域。|  
|[SaveToStream 方法](imetadataemit-savetostream-method.md)|將目前範圍中的所有中繼資料儲存至指定的 `IStream` 。|  
|[SetClassLayout 方法](imetadataemit-setclasslayout-method.md)|設定或更新先前呼叫所定義之型別的類別版面配置簽章 `IMetaDataEmit::DefineTypeDef` 。|  
|[SetCustomAttributeValue 方法](imetadataemit-setcustomattributevalue-method.md)|設定或更新先前呼叫所定義之自訂屬性的值 `IMetaDataEmit::DefineCustomAttribute` 。|  
|[SetEventProps 方法](imetadataemit-seteventprops-method.md)|設定或更新先前呼叫所定義之事件的指定功能 `IMetaDataEmit::DefineEvent` 。|  
|[SetFieldMarshal 方法](imetadataemit-setfieldmarshal-method.md)|針對指定之標記所參考的欄位、方法傳回或方法參數，設定 PInvoke 封送處理資訊。|  
|[SetFieldProps 方法](imetadataemit-setfieldprops-method.md)|設定或更新指定欄位標記所參考欄位的預設值。|  
|[SetFieldRVA 方法](imetadataemit-setfieldrva-method.md)|針對指定之標記所參考的欄位，設定其相對虛擬位址的全域變數值。|  
|[SetHandler 方法](imetadataemit-sethandler-method.md)|將指定指標所參考的方法設定 `IUnknown` 為 token 重新對應的通知回呼。|  
|[SetMethodImplFlags 方法](imetadataemit-setmethodimplflags-method.md)|設定或更新指定之標記所參考之繼承方法執行的中繼資料簽章。|  
|[SetMethodProps 方法](imetadataemit-setmethodprops-method.md)|設定或更新先前呼叫所定義之方法的功能，儲存在指定的相對虛擬位址 `IMetaDataEmit::DefineMethod` 。|  
|[SetModuleProps 方法](imetadataemit-setmoduleprops-method.md)|更新先前呼叫所定義之模組的參考 `IMetaDataEmit::DefineModuleRef` 。|  
|[SetParamProps 方法](imetadataemit-setparamprops-method.md)|設定或變更先前呼叫所定義之方法參數的功能 `IMetaDataEmit::DefineParam` 。|  
|[SetParent 方法](imetadataemit-setparent-method.md)|建立指定的成員（如先前的呼叫所定義） `IMetaDataEmit::DefineMemberRef` 是所指定類型的成員，如先前對的呼叫所定義 `IMetaDataEmit::DefineTypeDef` 。|  
|[SetPermissionSetProps 方法](imetadataemit-setpermissionsetprops-method.md)|設定或更新先前呼叫所定義之許可權集合的中繼資料簽章功能 `IMetaDataEmit::DefinePermissionSet` 。|  
|[SetPinvokeMap 方法](imetadataemit-setpinvokemap-method.md)|設定或變更方法的 PInvoke 簽章的功能，如先前的呼叫所定義 `IMetaDataEmit::DefinePinvokeMap` 。|  
|[SetPropertyProps 方法](imetadataemit-setpropertyprops-method.md)|針對先前呼叫所定義的屬性，設定儲存在中繼資料中的功能 `IMetaDataEmit::DefineProperty` 。|  
|[SetRVA 方法](imetadataemit-setrva-method.md)|設定指定方法的相對虛擬位址。|  
|[SetTypeDefProps 方法](imetadataemit-settypedefprops-method.md)|設定先前呼叫所定義之型別的功能 `IMetaDataEmit::DefineTypeDef` 。|  
|[TranslateSigWithScope 方法](imetadataemit-translatesigwithscope-method.md)|將元件匯入到目前的範圍，並為合併的範圍取得新的中繼資料簽章。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](metadata-interfaces.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
