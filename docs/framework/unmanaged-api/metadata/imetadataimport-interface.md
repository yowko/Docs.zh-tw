---
title: IMetaDataImport 介面
ms.date: 03/30/2017
api_name:
- IMetaDataImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport
helpviewer_keywords:
- IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0adbbd35-5e8d-4fec-8268-dc70a07c5975
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdea4c456f04911c37acd69ced65ba841f7959ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimport-interface"></a>IMetaDataImport 介面
提供從可攜式執行檔 (PE) 或其他來源匯入及管理現有中繼資料的方法，例如類型程式庫或獨立的執行階段中繼資料二進位檔。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CloseEnum 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|關閉具有指定控制代碼的列舉程式。|  
|[CountEnum 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|取得具有指定控制代碼之列舉程式中的項目數目。|  
|[EnumCustomAttributes 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|列舉與指定類型或成員相關聯的自訂屬性定義語彙基元清單。|  
|[EnumEvents 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|列舉指定 TypeDef 語彙基元的事件定義語彙基元。|  
|[EnumFields 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|列舉指定 TypeDef 語彙基元所參考類型的 FieldDef 語彙基元。|  
|[EnumFieldsWithName 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|列舉具有指定名稱之指定類型的 FieldDef 語彙基元。|  
|[EnumInterfaceImpls 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|列舉代表介面實作的 MethodDef 語彙基元。|  
|[EnumMemberRefs 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|列舉代表指定類型成員的 MemberRef 語彙基元。|  
|[EnumMembers 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|列舉代表指定類型成員的 MemberDef 語彙基元。|  
|[EnumMembersWithName 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|列舉 MemberDef 語彙基元，其代表具有指定名稱之指定類型成員。|  
|[EnumMethodImpls 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|列舉代表指定類型方法的 MethodBody 和 MethodDeclaration 語彙基元。|  
|[EnumMethods 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|列舉代表指定類型方法的 MethodDef 語彙基元。|  
|[EnumMethodSemantics 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|列舉和指定方法相關的屬性及屬性變更事件。|  
|[EnumMethodsWithName 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|列舉具有指定名稱的方法，且該方法由指定 TypeDef 語彙基元所參考的類型定義。|  
|[EnumModuleRefs 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|列舉代表已匯入的模組之 ModuleRef 語彙基元。|  
|[EnumParams 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|列舉 ParamDef 語彙基元，其代表指定 MethodDef 語彙基元所參考之方法的參數。|  
|[EnumPermissionSets 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|列舉指定中繼資料範圍內的物件權限。|  
|[EnumProperties 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|列舉 PropertyDef 語彙基元，其代表指定的 TypeDef 語彙基元所參考的類型屬性。|  
|[EnumSignatures 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|列舉代表目前範圍中獨立簽章的簽章語彙基元。|  
|[EnumTypeDefs 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|列舉代表目前範圍內的所有類型的 TypeDef 語彙基元。|  
|[EnumTypeRefs 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|列舉在目前中繼資料範圍中定義的 TypeRef 語彙基元。|  
|[EnumTypeSpecs 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|列舉在目前中繼資料範圍中定義的 TypeSpec 語彙基元。|  
|[EnumUnresolvedMethods 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|列舉 MemberDef 語彙基元，其代表目前中繼資料範圍內無法解析的方法。|  
|[EnumUserStrings 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|列舉字串語彙基元，其代表目前中繼資料範圍內的硬式編碼字串。|  
|[FindField 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|取得欄位的 FieldDef 語彙基元，該欄位為指定類型的成員，且具有指定名稱和中繼資料簽章。|  
|[FindMember 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|取得成員的 MemberDef 語彙基元指標，該成員由具有指定名稱和中繼資料簽章的指定類型所定義。|  
|[FindMemberRef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|取得成員的 MemberRef 語彙基元指標，該成員由具有指定名稱和中繼資料簽章的指定類型所定義。|  
|[FindMethod 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|取得方法的 MethodDef 語彙基元指標，該方法由具有指定名稱和中繼資料簽章的指定類型所定義。|  
|[FindTypeDefByName 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|取得具有指定名稱之類型的 TypeDef 中繼資料語彙基元的指標。|  
|[FindTypeRef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|取得 TypeRef 中繼資料語彙基元在指定搜尋範圍中參考具有指定名稱類型的指標。|  
|[GetClassLayout 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|取得指定 TypeDef 語彙基元所參考類別的配置資訊。|  
|[GetCustomAttributeByName 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|根據提供的名稱，取得自訂屬性的值。|  
|[GetCustomAttributeProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|根據提供的中繼資料語彙基元，取得自訂屬性的值。|  
|[GetEventProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|取得指定事件語彙基元所代表事件的中繼資料資訊 (包含宣告類型、委派的加入和移除方法，以及任何旗標和其他相關聯的資料)。|  
|[GetFieldMarshal 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|取得指定欄位中繼資料語彙基元所代表欄位的原生 Unmanaged 類型指標。|  
|[GetFieldProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|取得與指定 FieldDef 語彙基元所參考欄位相關聯的中繼資料。|  
|[GetInterfaceImplProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|取得實作指定方法的類型和宣告該方法的介面之中繼資料語彙基元指標。|  
|[GetMemberProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|取得指定中繼資料語彙基元所參考的類型成員中繼資料資訊 (包含名稱、二進位簽章和相對虛擬位址)。|  
|[GetMemberRefProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|取得與指定語彙基元所參考成員相關聯的中繼資料。|  
|[GetMethodProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|取得與指定 MethodDef 語彙基元所參考方法相關聯的中繼資料。|  
|[GetMethodSemantics 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|取得指定 MethodDef 語彙基元和成對屬性所參考的方法與指定 EventProp 所參考事件之間的關聯性指標。|  
|[GetModuleFromScope 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|取得在目前中繼資料範圍中所參考模組的中繼資料語彙基元指標。|  
|[GetModuleRefProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|取得指定中繼資料語彙基元所參考的模組名稱。|  
|[GetNameFromToken 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|取得指定中繼資料語彙基元所參考物件的 UTF-8 名稱。|  
|[GetNativeCallConvFromSig 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|取得由指定簽章指標代表的方法之原生呼叫慣例。|  
|[GetNestedClassProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|取得指定巢狀類型之封入父類型的 TypeDef 語彙基元。|  
|[GetParamForMethodIndex 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|取得代表在方法參數序列中指定序數位置參數的語彙基元指標，該序列為指定 MethodDef 語彙基元所代表方法的方法參數序列。|  
|[GetParamProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|取得指定 ParamDef 語彙基元所參考參數的中繼資料值。|  
|[GetPermissionSetProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|取得與指定權限語彙基元所代表之 System.Security.PermissionSet 相關聯的中繼資料。|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|取得 ModuleRef 語彙基元以代表 PInvoke 呼叫的目標組件。|  
|[GetPropertyProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|取得與指定語彙基元所代表屬性相關聯的中繼資料。|  
|[GetRVA 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|取得指定語彙基元所代表程式碼物件的相對虛擬位址的位移。|  
|[GetScopeProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|取得目前中繼資料範圍內組件或模組的名稱以及選擇性地取得其版本識別項。|  
|[GetSigFromToken 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|取得與指定語彙基元相關聯的二進位中繼資料簽章。|  
|[GetTypeDefProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|傳回指定 TypeDef 語彙基元所代表類型的中繼資料資訊。|  
|[GetTypeRefProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|取得與指定 TypeRef 語彙基元所參考類型相關聯的中繼資料。|  
|[GetTypeSpecFromToken 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|取得指定語彙基元所代表類型規格的二進位中繼資料簽章。|  
|[GetUserString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|取得指定中繼資料語彙基元所代表的常值字串。|  
|[IsGlobal 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|取得一個值，用來表示指定中繼資料語彙基元所代表的欄位、方法或類型值是否具有全域範圍。|  
|[IsValidToken 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|取得一個值，用來表示指定語彙基元是否包含程式碼物件的有效參考。|  
|[ResetEnum 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|重設指定列舉程式至指定位置。|  
|[ResolveTypeRef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|取得指定 TypeRef 語彙基元所參考類型的類型資訊。|  
  
## <a name="remarks"></a>備註  
 `IMetaDataImport` 介面的設計主要是讓工具和服務使用，這些會匯入類型資訊 (例如開發工具) 或管理已部署的元件 (例如解析/啟用服務)。 `IMetaDataImport` 中的方法可分成下列工作分類：  
  
-   列舉中繼資料範圍內的項目集合。  
  
-   尋找具有一組特定特性的項目。  
  
-   取得指定項目的屬性。  
  
-   Get 方法是專門用來傳回中繼資料項目的單一值屬性。 當屬性為另一個項目的參考時，則會傳回該項目的語彙基元。 任何指標輸入類型都可以是 NULL，表示未要求特定的值。 若要取得基本上是集合物件的屬性 (例如類別實作的介面集合)，請使用列舉方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
