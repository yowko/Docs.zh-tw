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
ms.openlocfilehash: 8d9de753f1c44338a96e990def80643d591f2a8b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007464"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope 方法
開啟現有的磁片上檔案，並將其中繼資料對應至記憶體。  
  
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
 在要開啟的檔案名。 檔案必須包含 common language runtime （CLR）中繼資料。  
  
 `dwOpenFlags`  
 在[CorOpenFlags](coropenflags-enumeration.md)列舉的值，用來指定要開啟的模式（讀取、寫入等等）。  
  
 `riid`  
 在要傳回之所需中繼資料介面的 IID;呼叫端會使用介面來匯入（讀取）或發出（寫入）中繼資料。  
  
 的值 `riid` 必須指定其中一個「匯入」或「發出」介面。 有效的值為 IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2 或 IID_IMetaDataImport2。  
  
 `ppIUnk`  
 脫銷傳回之介面的指標。  
  
## <a name="remarks"></a>備註  
 您可以使用其中一個「匯入」介面的方法來查詢中繼資料的記憶體中複本，或使用其中一個「發出」介面中的方法將其新增至。  
  
 如果目標檔案不包含 CLR 中繼資料，此 `OpenScope` 方法將會失敗。  
  
 在 .NET Framework 版本1.0 和1.1 版中，如果已開啟範圍並 `dwOpenFlags` 將設定為 ofRead，它就符合共用資格。 也就是說，如果後續的呼叫 `OpenScope` 傳入先前開啟之檔案的名稱，就會重複使用現有的範圍，並不會建立一組新的資料結構。 不過，由於此共用，可能會發生問題。  
  
 在 .NET Framework 版本2.0 中， `dwOpenFlags` 已不再共用以設定為 ofRead 開啟的範圍。 使用 ofReadOnly 值可允許共用範圍。 共用範圍時，使用「讀取/寫入」中繼資料介面的查詢將會失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataDispenser 介面](imetadatadispenser-interface.md)
- [IMetaDataDispenserEx 介面](imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport 介面](imetadataassemblyimport-interface.md)
- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
