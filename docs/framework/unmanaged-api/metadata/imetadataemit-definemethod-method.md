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
ms.openlocfilehash: d4f3c95428d6f0f8807e284c5b54582428176511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177671"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod 方法
使用指定簽名的方法或全域函數創建定義，並將權杖返回到該方法定義。  
  
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
 [在]方法`mdTypedef`的父類或父介面的權杖。 如果要`td`定義`mdTokenNil`全域函數，則設置為 ，設置為 。。  
  
 `szName`  
 [在]Unicode 中的成員名稱。  
  
 `dwMethodFlags`  
 [在][CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)枚舉的值，用於指定方法或全域函數的屬性。  
  
 `pvSigBlob`  
 [在]方法簽名。 簽名將保留為提供。 如果需要為任何參數指定其他資訊，請使用[IMetaDataEmit：：setParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)方法。  
  
 `cbSigBlob`  
 [在]中的`pvSigBlob`位元組計數。  
  
 `ulCodeRVA`  
 [在]代碼的位址。  
  
 `dwImplFlags`  
 [在][CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)枚舉的值，用於指定方法的實現特徵。  
  
 `pmd`  
 [出]成員權杖。  
  
## <a name="remarks"></a>備註  
 中繼資料 API 保證以與調用方為給定的封閉類或介面發出方法的順序保留方法，該類或介面在`td`參數中指定。  
  
 有關 使用`DefineMethod`和特定參數設置的其他資訊，請參閱下文。  
  
## <a name="slots-in-the-v-table"></a>V 表中的插槽  
 運行時使用方法定義來設置 v 表槽。 如果需要跳過一個或多個插槽（例如，使用 COM 介面佈局保留同位），則定義虛擬方法以佔用 v 表中的插槽或插槽;例如，使用 COM 介面佈局保留同位，則使用虛擬方法佔用 v-table 中的插槽或插槽。將`dwMethodFlags`設置為`mdRTSpecialName`[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)枚舉的值，並將名稱指定為：  
  
 _VtblGap\<*序數*>\<*CountOfSlots*計數\_>
  
 *其中序列編號*是方法的序號 *，CountOfSlots*是 v 表中要跳過的插槽數。 如果省略*了 CountOflots，* 則假定為 1。 這些虛擬方法不能從託管或非託管代碼調用，任何嘗試調用它們（從託管代碼或非託管代碼）都會生成異常。 它們的唯一目的是佔用運行時為 COM 集成生成的 v 表中的空間。  
  
## <a name="duplicate-methods"></a>重複方法  
 不應定義重複的方法。 `DefineMethod`也就是說，不應使用`td`中`wzName`重複的值集調用 ， 和`pvSig`參數。 （這三個參數一起唯一地定義方法。 但是，可以使用重複的三重，前提是，對於方法定義之一，可以在`mdPrivateScope``dwMethodFlags`參數中設置位。 （該`mdPrivateScope`位表示編譯器不會發出對此方法定義的引用。  
  
## <a name="method-implementation-information"></a>方法實現資訊  
 在聲明方法時，通常不知道有關方法實現的資訊。 因此，調用 時不需要傳遞`ulCodeRVA`和`dwImplFlags`參數中的值。 `DefineMethod` 這些值稍後可以通過[IMetaDataEmit：：設置方法Implflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)或[IMetaDataEmit：：SetRVA，](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)視情況而定。  
  
 在某些情況下，如平台叫用 （PInvoke） 或 COM 互通方案，將不會提供方法正文，並且`ulCodeRVA`應設置為零。 在這些情況下，方法不應標記為抽象，因為運行時將定位實現。  
  
## <a name="defining-a-method-for-pinvoke"></a>定義 PInvoke 的方法  
 要通過 PInvoke 調用每個非託管函數，必須定義表示目標非託管函數的託管方法。 要定義託管方法，請使用`DefineMethod`設置為特定值的某些參數，具體取決於 PInvoke 的使用方式：  
  
- True PInvoke - 涉及調用駐留在非託管 DLL 中的外部非託管方法。  
  
- 本地 PInvoke - 涉及調用嵌入在當前託管模組中的本機非託管方法。  
  
 參數設置在下表中給出。  
  
|參數|真實 PInvoke 的值|本地 PInvoke 的值|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||設置`mdStatic`;清楚`mdSynchronized`和`mdAbstract`。|  
|`pvSigBlob`|有效的通用語言運行時 （CLR） 方法簽名，具有有效的託管類型的參數。|具有有效託管類型的參數的有效 CLR 方法簽名。|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|請設定 `miCil` 和 `miManaged`。|請設定 `miNative` 和 `miUnmanaged`。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
