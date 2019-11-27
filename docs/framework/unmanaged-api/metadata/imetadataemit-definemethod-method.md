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
ms.openlocfilehash: c46b075341742aac605537a08b762b3cf47ef35b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431812"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod 方法
使用指定的簽章建立方法或全域函式的定義，並將權杖傳回給該方法定義。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 在方法之父類別或父介面的 `mdTypedef` token。 如果您要定義全域函式，請將 `td` 設定為 `mdTokenNil`。  
  
 `szName`  
 在Unicode 中的成員名稱。  
  
 `dwMethodFlags`  
 在[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列舉的值，指定方法或全域函數的屬性。  
  
 `pvSigBlob`  
 在方法簽章。 簽章會以提供的方式保存。 如果您需要指定任何參數的其他資訊，請使用[IMetaDataEmit：： SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)方法。  
  
 `cbSigBlob`  
 在`pvSigBlob`中的位元組計數。  
  
 `ulCodeRVA`  
 在程式碼的位址。  
  
 `dwImplFlags`  
 在[CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)列舉的值，指定方法的實功能。  
  
 `pmd`  
 脫銷成員 token。  
  
## <a name="remarks"></a>備註  
 中繼資料 API 保證保存方法的順序，與呼叫者針對指定的封入類別或介面（在 `td` 參數中指定）發出的相同。  
  
 以下提供有關使用 `DefineMethod` 和特定參數設定的其他資訊。  
  
## <a name="slots-in-the-v-table"></a>V 資料表中的插槽  
 執行時間會使用方法定義來設定 v 資料表位置。 在需要略過一個或多個位置的情況下（例如，為了保留與 COM 介面配置的同位），會定義虛擬方法，以佔用 v 資料表中的位置或插槽;將 `dwMethodFlags` 設定為[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列舉的 `mdRTSpecialName` 值，並將此名稱指定為：  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 其中*SequenceNumber*是方法的序號，而*CountOfSlots*是要在 v 資料表中略過的位置數目。 如果省略*CountOfSlots* ，則會假設為1。 這些虛擬方法無法從 managed 或非受控程式碼呼叫，而任何嘗試從 managed 或非受控程式碼呼叫它們都會產生例外狀況。 其唯一的目的是要佔用執行時間為 COM 整合而產生的 v 資料表空間。  
  
## <a name="duplicate-methods"></a>重複的方法  
 您不應該定義重複的方法。 也就是說，您不應該在 `td`、`wzName`和 `pvSig` 參數中，使用一組重複的值來呼叫 `DefineMethod`。 （這三個參數會一起唯一定義方法）。 不過，您可以使用重複的三重，在其中一個方法定義中，您可以在 `dwMethodFlags` 參數中設定 `mdPrivateScope` 位。 （`mdPrivateScope` 位表示編譯器不會發出這個方法定義的參考）。  
  
## <a name="method-implementation-information"></a>方法執行資訊  
 在宣告方法時，通常不知道方法執行的相關資訊。 因此，在呼叫 `DefineMethod`時，您不需要在 `ulCodeRVA` 中傳遞值，並 `dwImplFlags` 參數。 稍後可以視需要透過[IMetaDataEmit：： SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)或[IMetaDataEmit：： SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)來提供值。  
  
 在某些情況下（例如平台叫用（PInvoke）或 COM Interop 案例），將不會提供方法主體，而且 `ulCodeRVA` 應該設定為零。 在這些情況下，方法不應標記為抽象，因為執行時間會找出該實作為。  
  
## <a name="defining-a-method-for-pinvoke"></a>定義 PInvoke 的方法  
 針對要透過 PInvoke 呼叫的每個非受控函式，您必須定義代表目標非受控函式的 managed 方法。 若要定義 managed 方法，請使用 `DefineMethod`，並將一些參數設定為特定值，視使用 PInvoke 的方式而定：  
  
- True PInvoke-牽涉到位於非受控 DLL 中的外部非受控方法調用。  
  
- 本機 PInvoke-牽涉到內嵌在目前受管理模組中的原生非受控方法調用。  
  
 下表提供參數設定。  
  
|參數|True PInvoke 的值|本機 PInvoke 的值|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||設定 `mdStatic`;清除 `mdSynchronized` 和 `mdAbstract`。|  
|`pvSigBlob`|有效的 common language runtime （CLR）方法簽章，其參數為有效的 managed 類型。|有效的 CLR 方法簽章，其參數為有效的 managed 類型。|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|設定 `miCil` 和 `miManaged`。|設定 `miNative` 和 `miUnmanaged`。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
