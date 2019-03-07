---
title: IMetaDataDispenser::OpenScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4ffbd2bc3042f7e37e90dceeb28ec50b3c73cef
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491967"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope 方法
開啟現有磁碟上的檔案，並將它的中繼資料對應到記憶體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>參數  
 `szScope`  
 [in]要開啟之檔案的名稱。 此檔案必須包含 common language runtime (CLR) 中繼資料。  
  
 `dwOpenFlags`  
 [in]值為[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)列舉，來開啟指定的模式 （讀取、 寫入和等等）。  
  
 `riid`  
 [in]要傳回; 所需的中繼資料介面的 IID呼叫端會使用介面來匯入 （讀取），或發出 （寫入） 的中繼資料。  
  
 值`riid`必須指定其中一個 「 匯入 」 或 「 發出 」 介面。 有效值為 IID_IMetaDataEmit、 IID_IMetaDataImport、 IID_IMetaDataAssemblyEmit、 IID_IMetaDataAssemblyImport、 IID_IMetaDataEmit2 或 IID_IMetaDataImport2。  
  
 `ppIUnk`  
 [out]要傳回的介面的指標。  
  
## <a name="remarks"></a>備註  
 使用方法的其中一個 「 匯入 」 介面，或新增要使用的 「 發出 」 介面的其中一個方法，您可以查詢中繼資料的記憶體內的複本。  
  
 如果目標檔案不包含 CLR 中繼資料，`OpenScope`方法將會失敗。  
  
 在.NET Framework 1.0 和 1.1 中，如果範圍與開啟`dwOpenFlags`設 ofRead，很適合共用。 也就是說，如果後續呼叫`OpenScope`傳入名稱先前已開啟的檔案，會重複使用現有的範圍，並不會建立一組新的資料結構。 不過，由於此共用可能會發生問題。  
  
 在.NET Framework 2.0 版中，範圍則是使用開啟`dwOpenFlags`設 ofRead 不再共用。 若要允許共用範圍使用 ofReadOnly 值。 共用範圍時，使用 [讀取/寫入] 中繼資料介面的查詢將會失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
