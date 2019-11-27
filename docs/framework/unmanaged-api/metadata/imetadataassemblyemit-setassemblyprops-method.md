---
title: IMetaDataAssemblyEmit::SetAssemblyProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
ms.openlocfilehash: f79320d5b7d2ad4ad44a79fae063ce6718490a70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431957"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyProps 方法
修改指定的 `Assembly` 中繼資料結構。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `pma`  
 在元資料標記，指定要修改的 `Assembly` 元資料結構。  
  
 `pbPublicKey`  
 在元件發行者公用金鑰的指標。  
  
 `cbPublicKey`  
 在`pbPublicKey`的大小（以位元組為單位）。  
  
 `ulHashAlgId`  
 在用來雜湊元件檔的雜湊演算法識別碼。  
  
 `szName`  
 在元件的人類看得懂的文字名稱。  
  
 `pMetaData`  
 在ASSEMBLYMETADATA 的指標，其中包含元件的版本、平臺和地區設定資訊。  
  
 `dwAssemblyFlags`  
 在[AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)值的位元組合，這個組合會指定元件的各種屬性。  
  
## <a name="remarks"></a>備註  
 若要建立 `Assembly` 元資料結構，請使用[IMetaDataAssemblyEmit：:D efineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
