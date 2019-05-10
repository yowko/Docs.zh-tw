---
title: IMetaDataEmit::DefineMethod 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4879af90aa06515a95b4d15f039ff3c2b1a88f62
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665010"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod 方法
使用指定的簽章中，建立方法或全域函式的定義，並將權杖傳回給該方法的定義。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 [in]`mdTypedef`語彙基元的父類別或方法的父介面。 設定`td`至`mdTokenNil`，如果您正在定義全域函式。  
  
 `szName`  
 [in]以 Unicode 成員名稱。  
  
 `dwMethodFlags`  
 [in]值為[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列舉，指定方法或全域函式的屬性。  
  
 `pvSigBlob`  
 [in]方法簽章。 提供，則會保存簽章。 如果您需要指定任何參數的其他資訊，請使用[imetadataemit:: Setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)方法。  
  
 `cbSigBlob`  
 [in]中的位元組計數`pvSigBlob`。  
  
 `ulCodeRVA`  
 [in]程式碼的位址。  
  
 `dwImplFlags`  
 [in]值為[CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)列舉，指定方法的實作功能。  
  
 `pmd`  
 [out]成員語彙基元。  
  
## <a name="remarks"></a>備註  
 保存方法的相同順序，因為呼叫端會將它們發出指定封入類別或介面中所指定的中繼資料 API 可保證`td`參數。  
  
 使用有關的其他資訊`DefineMethod`和特定的參數設定如下。  
  
## <a name="slots-in-the-v-table"></a>V 資料表中的位置  
 執行階段會使用方法定義，來設定 v-table 位置。 在其中一個或多個位置需要略過，這類情況下對於保留同位檢查 COM 介面的版面配置，虛擬方法定義為佔用的位置或 v-table; 中的位置設定`dwMethodFlags`要`mdRTSpecialName`的值[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列舉型別並將名稱指定為：  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 何處*SequenceNumber*是方法的序號和*CountOfSlots*會在 v-table 中略過的位置數目。 如果*CountOfSlots*已省略，則假設為 1。 這些虛擬方法不是可從 managed 或 unmanaged 程式碼呼叫，任何嘗試呼叫它們，從 managed 或 unmanaged 程式碼，就會產生例外狀況。 其唯一用途是佔用執行階段會產生 COM 整合 v 資料表中的空間。  
  
## <a name="duplicate-methods"></a>重複的方法  
 您不能定義重複的方法。 也就是說，您不應該呼叫`DefineMethod`與一組重複的值`td`， `wzName`，和`pvSig`參數。 (這三個參數一起唯一定義的方法。)。 不過，使用重複的三倍，前提是，在您設定的其中一個方法定義，`mdPrivateScope`位元`dwMethodFlags`參數。 (`mdPrivateScope`位元表示編譯器將不會發出這個方法定義的參考。)  
  
## <a name="method-implementation-information"></a>方法的實作資訊  
 在此方法宣告的時間通常不知道方法實作的相關資訊。 因此，您不需要傳遞值`ulCodeRVA`並`dwImplFlags`參數呼叫時`DefineMethod`。 提供值的順序可以稍後透過[imetadataemit:: Setmethodimplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)或是[imetadataemit:: Setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)視需要。  
  
 在某些情況下，例如平台叫用 (PInvoke) 或 COM interop 案例中，不會提供方法主體，以及`ulCodeRVA`應該設定為零。 在這些情況下，此方法不應標記為抽象，因為執行階段會找出實作。  
  
## <a name="defining-a-method-for-pinvoke"></a>定義方法的 PInvoke  
 對於透過 PInvoke 呼叫每個 unmanaged 函式，您必須定義受管理的方法，表示目標 unmanaged 函式。 若要定義受管理的方法，使用`DefineMethod`與某些參數設為特定值，根據在其中使用 PInvoke 的方式：  
  
- True PInvoke-涉及在 unmanaged DLL 位於外部的 unmanaged 方法引動過程。  
  
- 本機 PInvoke-包含內嵌於目前的受管理模組中的原生 unmanaged 方法的引動過程。  
  
 下表提供的參數設定。  
  
|參數|值，則為 true 的 PInvoke|本機 PInvoke 的值|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||設定`mdStatic`; 清除`mdSynchronized`和`mdAbstract`。|  
|`pvSigBlob`|有效 common language runtime (CLR) 方法簽章具有有效的參數將 managed 型别。|有效的 CLR 方法簽章，以有效的參數將 managed 型别。|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|設定`miCil`和`miManaged`。|設定`miNative`和`miUnmanaged`。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
