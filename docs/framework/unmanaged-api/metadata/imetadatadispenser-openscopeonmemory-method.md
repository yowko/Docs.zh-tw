---
title: IMetaDataDispenser::OpenScopeOnMemory 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 04e0fabfc0d70c9d922e0715f32bd07237ce8741
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442318"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a>IMetaDataDispenser::OpenScopeOnMemory 方法
開啟包含現有中繼資料的記憶體區域。 也就是說，這個方法會開啟指定的記憶體區域，其中現有的資料會被視為中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>參數  
 `pData`  
 在指標，指定記憶體區域的起始位址。  
  
 `cbData`  
 在記憶體區域的大小（以位元組為單位）。  
  
 `dwOpenFlags`  
 在[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)列舉的值，用來指定要開啟的模式（讀取、寫入等等）。  
  
 `riid`  
 在要傳回之所需中繼資料介面的 IID;呼叫端會使用介面來匯入（讀取）或發出（寫入）中繼資料。  
  
 `riid` 的值必須指定其中一個「匯入」或「發出」介面。 有效的值為 IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2 或 IID_IMetaDataImport2。  
  
 `ppIUnk`  
 脫銷傳回之介面的指標。  
  
## <a name="remarks"></a>備註  
 您可以使用其中一個「匯入」介面的方法來查詢中繼資料的記憶體中複本，或使用其中一個「發出」介面中的方法將其新增至。  
  
 `OpenScopeOnMemory` 方法類似于[IMetaDataDispenser：： OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法，不同之處在于有興趣的中繼資料已存在於記憶體中，而不是磁片上的檔案中。  
  
 如果記憶體的目的地區域不包含 common language runtime （CLR）中繼資料，`OpenScopeOnMemory` 方法將會失敗。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
