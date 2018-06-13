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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f184c04db384c2b9bdbce2d8ae6919c05a2ab425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448891"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a>IMetaDataDispenser::OpenScopeOnMemory 方法
開啟包含現有的中繼資料的記憶體區域。 也就是說，這個方法會開啟指定的現有資料會被視為中繼資料的記憶體區域。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pData`  
 [in]指定的記憶體區域的起始位址指標。  
  
 `cbData`  
 [in]記憶體區域，以位元組為單位的大小。  
  
 `dwOpenFlags`  
 [in]值為[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)列舉來指定 （讀取、 寫入和等等） 的模式開啟。  
  
 `riid`  
 [in]要傳回; 所需的中繼資料介面的 IID呼叫端會使用介面來匯入 （讀取），或發出 （寫入） 中繼資料。  
  
 值`riid`必須指定其中一個 「 匯入 」 或 「 發出"介面。 有效值為 IID_IMetaDataEmit、 IID_IMetaDataImport、 IID_IMetaDataAssemblyEmit、 IID_IMetaDataAssemblyImport、 IID_IMetaDataEmit2 或 IID_IMetaDataImport2。  
  
 `ppIUnk`  
 [out]要傳回的介面的指標。  
  
## <a name="remarks"></a>備註  
 您可以查詢中繼資料的記憶體中複本，使用其中一個，「 匯入 」 的介面方法，或加入至一個 「 發出"介面的使用方法。  
  
 `OpenScopeOnMemory`方法很類似[imetadatadispenser:: Openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法，不同之處在於感興趣的中繼資料已存在的記憶體，而不是磁碟上的檔案。  
  
 如果記憶體目標區域不包含 common language runtime (CLR) 中繼資料，`OpenScopeOnMemory`方法將會失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [IMetaDataDispenserEx 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
