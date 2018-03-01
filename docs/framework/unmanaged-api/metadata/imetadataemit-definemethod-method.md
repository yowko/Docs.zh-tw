---
title: "IMetaDataEmit::DefineMethod 方法"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4fa136f5e6669e58ef709db5b53f538804cfcac2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod 方法
建立方法或全域函式的定義與指定的簽章，並傳回該方法定義的語彙基元。  
  
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
  
#### <a name="parameters"></a>參數  
 `td`  
 [in]`mdTypedef`語彙基元之父類別或方法的父介面。 設定`td`至`mdTokenNil`，如果您正在定義全域函式。  
  
 `szName`  
 [in]以 Unicode 成員名稱。  
  
 `dwMethodFlags`  
 [in]值為[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列舉，指定方法或全域函式的屬性。  
  
 `pvSigBlob`  
 [in]方法簽章。 簽章會保存提供的一樣。 如果您要指定任何參數的其他資訊，請使用[imetadataemit:: Setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)方法。  
  
 `cbSigBlob`  
 [in]中的位元組計數`pvSigBlob`。  
  
 `ulCodeRVA`  
 [in]程式碼的位址。  
  
 `dwImplFlags`  
 [in]值為[CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)列舉，指定方法的實作功能。  
  
 `pmd`  
 [out]成員語彙基元。  
  
## <a name="remarks"></a>備註  
 中繼資料 API 會確保保存相同順序的方法呼叫端指定封入類別或介面中所指定發出`td`參數。  
  
 使用有關的其他資訊`DefineMethod`，如下所示的特定參數設定。  
  
## <a name="slots-in-the-v-table"></a>在 v-table 中的位置  
 執行階段會使用方法定義，來設定 v-table 位置。 在其中一個或多個位置需要略過，這類情況下保留同位檢查 COM 介面的版面配置，但對於 dummy 方法定義成採用位置或 v-table; 中的位置設定`dwMethodFlags`至`mdRTSpecialName`值[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列舉和指定名稱為：  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>  
  
 其中*SequenceNumber*是方法的序號和*CountOfSlots*是要在 v-table 中略過的位置數目。 如果*CountOfSlots*已省略，則假設為 1。 這些虛擬方法不可以從 managed 或 unmanaged 程式碼呼叫，任何嘗試從 managed 或 unmanaged 程式碼呼叫它們，就會產生例外狀況。 其唯一用途就是以使用執行階段產生 COM 整合 v 資料表中的空間。  
  
## <a name="duplicate-methods"></a>重複的方法  
 您不應定義重複的方法。 也就是說，您不應該呼叫`DefineMethod`與一組重複的值在`td`， `wzName`，和`pvSig`參數。 (這三個參數一起唯一定義的方法。)。 不過，使用重複的三倍，前提為其中一個方法定義中，設定`mdPrivateScope`位元`dwMethodFlags`參數。 (`mdPrivateScope`位元表示編譯器將不會發出這個方法定義的參考。)  
  
## <a name="method-implementation-information"></a>方法實作資訊  
 在方法宣告為階段，通常不為已知方法實作的相關資訊。 因此，您不需要將值在傳遞`ulCodeRVA`和`dwImplFlags`參數呼叫時`DefineMethod`。 提供值的順序可以稍後透過[imetadataemit:: Setmethodimplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)或[imetadataemit:: Setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)視情況。  
  
 在某些情況下，例如平台引動過程 (PInvoke) 或 COM interop 案例中，不會提供方法主體，以及`ulCodeRVA`應該設定為零。 在這些情況下，此方法不應標記為抽象，因為執行階段會尋找實作。  
  
## <a name="defining-a-method-for-pinvoke"></a>定義方法為 PInvoke  
 對於透過 PInvoke 呼叫每個 unmanaged 函式，您必須定義受管理的方法，表示目標 unmanaged 函式。 若要定義受管理的方法，請使用`DefineMethod`與某些參數設為特定值，視 PInvoke 中使用的方式而定：  
  
-   True PInvoke-牽涉到位於 unmanaged DLL 中的外部的 unmanaged 方法的引動過程。  
  
-   本機 PInvoke-包含內嵌在目前的受管理模組的原生 unmanaged 方法的引動過程。  
  
 下表提供的參數設定。  
  
|參數|值，則為 true 的 PInvoke|本機 PInvoke 值|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||設定`mdStatic`; 清除`mdSynchronized`和`mdAbstract`。|  
|`pvSigBlob`|有效 common language runtime (CLR) 方法簽章以有效的參數將 managed 類型。|有效的 CLR 方法簽章，以有效的參數將 managed 類型。|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|設定`miCil`和`miManaged`。|設定`miNative`和`miUnmanaged`。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
