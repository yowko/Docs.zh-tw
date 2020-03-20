---
title: IMetaDataDispenser::DefineScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
ms.openlocfilehash: 2f9325f3795262a0c33af02f87fc5d3a020658cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177646"
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope 方法
在記憶體中創建一個新區域，您可以在其中創建新中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>參數  
 `rclsid`  
 [在]要創建的元資料結構版本的 CLSID。 此值必須CLSID_CorMetaDataRuntime .NET 框架版本 2.0。  
  
 `dwCreateFlags`  
 [在]指定選項的標誌。 此值對於 .NET 框架 2.0 必須為零。  
  
 `riid`  
 [在]要返回的所需中繼資料介面的 IID;調用方將使用介面創建新中繼資料。  
  
 的值`riid`必須指定其中一個"emit"介面。 有效值IID_IMetaDataEmit、IID_IMetaDataAssemblyEmit 或IID_IMetaDataEmit2。  
  
 `ppIUnk`  
 [出]指向返回介面的指標。  
  
## <a name="remarks"></a>備註  
 `DefineScope`創建一組記憶體中中繼資料表，為中繼資料生成唯一 GUID（模組版本識別碼或 MVID），並在模組表中為發出的編譯單元創建一個條目。  
  
 您可以根據需要使用[IMetaDataEmit：setModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)或[IMetaDataEmit：:DefineCustom屬性](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)方法將屬性附加到整個中繼資料範圍。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
