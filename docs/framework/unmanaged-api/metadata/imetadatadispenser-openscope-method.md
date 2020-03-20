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
ms.openlocfilehash: 5185fb6663910c85ce5dae1225b9b10c5dd8bb28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175937"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope 方法
打開現有的磁片檔並將其元資料對應到記憶體中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>參數  
 `szScope`  
 [在]要打開的檔的名稱。 該檔必須包含通用語言運行時 （CLR） 中繼資料。  
  
 `dwOpenFlags`  
 [在][CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)枚舉的值，用於指定打開的模式（讀取、寫入等）。  
  
 `riid`  
 [在]要返回的所需中繼資料介面的 IID;調用方將使用介面導入（讀取）或發出（寫入）中繼資料。  
  
 的值`riid`必須指定其中一個"導入"或"發射"介面。 有效值IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2或IID_IMetaDataImport2。  
  
 `ppIUnk`  
 [出]指向返回介面的指標。  
  
## <a name="remarks"></a>備註  
 可以使用"導入"介面之一的方法查詢中繼資料的記憶體副本，也可以添加到使用"emit"介面之一的方法。  
  
 如果目的檔案不包含 CLR 中繼資料，則`OpenScope`該方法將失敗。  
  
 在 .NET 框架版本 1.0 和版本 1.1 中，`dwOpenFlags`如果使用設置為 Read 打開作用域，則它有資格共用。 也就是說，如果後續調用以`OpenScope`以前打開的檔的名稱傳遞，則重用現有作用域，並且不會創建新的資料結構集。 但是，由於這種共用，可能會出現問題。  
  
 在 .NET 框架版本 2.0 中，`dwOpenFlags`不再共用使用設置為 Read 打開的作用域。 使用 ReadOnly 值允許共用作用域。 共用作用域時，使用"讀/寫"中繼資料介面的查詢將失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
