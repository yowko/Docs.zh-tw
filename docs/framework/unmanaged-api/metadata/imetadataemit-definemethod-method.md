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
ms.openlocfilehash: a32a1eb850943b84a0d368f883e44fd4ccf32ee9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719576"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod 方法

使用指定的簽章來建立方法或全域函式的定義，並將標記傳回至該方法定義。  
  
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
 在 `mdTypedef` 方法的父類別或父介面的標記。 `td` `mdTokenNil` 如果您要定義全域函數，請將設定為。  
  
 `szName`  
 在Unicode 中的成員名稱。  
  
 `dwMethodFlags`  
 在 [CorMethodAttr](cormethodattr-enumeration.md) 列舉的值，可指定方法或全域函式的屬性。  
  
 `pvSigBlob`  
 在方法簽章。 簽章會依照提供的方式保存。 如果您需要指定任何參數的其他資訊，請使用 [IMetaDataEmit：： SetParamProps](imetadataemit-setparamprops-method.md) 方法。  
  
 `cbSigBlob`  
 在中的位元組計數 `pvSigBlob` 。  
  
 `ulCodeRVA`  
 在程式碼的位址。  
  
 `dwImplFlags`  
 在 [CorMethodImpl](cormethodimpl-enumeration.md) 列舉的值，可指定方法的執行功能。  
  
 `pmd`  
 擴展成員 token。  
  
## <a name="remarks"></a>備註  

 中繼資料 API 可保證保存方法的順序，與呼叫者針對指定的封閉類別或介面（在參數中所指定）發出時相同 `td` 。  
  
 `DefineMethod`以下提供有關使用和特定參數設定的其他資訊。  
  
## <a name="slots-in-the-v-table"></a>V 資料表中的插槽  

 執行時間會使用方法定義來設定 v 資料表的位置。 在需要略過一或多個位置的情況下（例如，為了保留與 COM 介面配置的同位），會定義虛擬方法，以佔用 v 資料表中的位置或插槽;將設定 `dwMethodFlags` 為 `mdRTSpecialName` [CorMethodAttr](cormethodattr-enumeration.md) 列舉的值，並將名稱指定為：  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 其中 *SequenceNumber* 是方法的序號，而 *CountOfSlots* 是要在 v 資料表中略過的位置數目。 如果省略 *CountOfSlots* ，則會假設為1。 這些虛擬方法無法從 managed 或非受控碼進行呼叫，而且任何從 managed 或非受控碼呼叫它們的嘗試都會產生例外狀況。 其唯一目的是要佔用執行時間為 COM 整合所產生之 v 資料表中的空間。  
  
## <a name="duplicate-methods"></a>重複的方法  

 您不應該定義重複的方法。 也就是說，您不應該 `DefineMethod` 使用 `td` 、和參數中的一組重複值來呼叫 `wzName` `pvSig` 。  (這三個參數一起唯一定義方法。 ) 。 不過，您可以使用重複的三重，在其中一個方法定義中，您可以 `mdPrivateScope` 在參數中設定位 `dwMethodFlags` 。  (`mdPrivateScope` 位表示編譯器將不會發出此方法定義的參考。 )   
  
## <a name="method-implementation-information"></a>方法執行資訊  

 在宣告方法時，通常不知道方法執行的相關資訊。 因此，當您呼叫時，不需要在和參數中傳遞值 `ulCodeRVA` `dwImplFlags` `DefineMethod` 。 您可以視需要透過 [IMetaDataEmit：： SetMethodImplFlags](imetadataemit-setmethodimplflags-method.md) 或 [IMetaDataEmit：： SetRVA](imetadataemit-setrva-method.md)提供這些值。  
  
 在某些情況下（例如平台叫用） (PInvoke) 或 COM interop 案例中，將不會提供方法主體，而且 `ulCodeRVA` 應設為零。 在這些情況下，方法不應標記為抽象，因為執行時間會找出執行。  
  
## <a name="defining-a-method-for-pinvoke"></a>定義 PInvoke 的方法  

 針對透過 PInvoke 呼叫的每個非受控函式，您必須定義表示目標未受管理函數的 managed 方法。 若要定義 managed 方法，請使用， `DefineMethod` 並將某些參數設為特定值，視使用 PInvoke 的方式而定：  
  
- True PInvoke-牽涉到位於非受控 DLL 中的外部非受控方法的調用。  
  
- Local PInvoke-牽涉到內嵌于目前受管理模組中的原生非受控方法的調用。  
  
 下表提供參數設定。  
  
|參數|True PInvoke 的值|本機 PInvoke 的值|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Set `mdStatic` ; clear `mdSynchronized` 和 `mdAbstract` 。|  
|`pvSigBlob`|有效的 common language runtime (CLR) 方法簽章，其參數為有效的 managed 類型。|具有有效 managed 類型之參數的有效 CLR 方法簽章。|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|請設定 `miCil` 和 `miManaged`。|請設定 `miNative` 和 `miUnmanaged`。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
