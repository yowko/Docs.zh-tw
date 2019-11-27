---
title: IMetaDataAssemblyEmit::DefineAssembly 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 20628e708261076c6e172ff30c366a0d69c2e0f2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432116"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly 方法
建立 `Assembly` 結構，其中包含指定元件的中繼資料，並傳回相關聯的元資料標記。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbPublicKey`  
 在識別元件發行者的公開金鑰; 如果元件不是強式名稱，則為 Null。  
  
 `cbPublicKey`  
 在`pbPublicKey`的大小（以位元組為單位）。  
  
 `uHashAlgId`  
 在要用來加密元件中之檔案的雜湊演算法識別碼，或為 Null 以指定 SHA-1 演算法。  
  
 `szName`  
 在元件的人類看得懂的文字名稱。 此值不得超過1024個字元。  
  
 `pMetaData`  
 在ASSEMBLYMETADATA 實例的指標，其中包含元件的版本、平臺和地區設定資訊。  
  
 `dwAssemblyFlags`  
 在描述元件功能的[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值組合。  
  
 `pmda`  
 脫銷元資料標記的指標。  
  
## <a name="remarks"></a>備註  
 資訊清單中只能定義一個 `Assembly` 元資料結構。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
