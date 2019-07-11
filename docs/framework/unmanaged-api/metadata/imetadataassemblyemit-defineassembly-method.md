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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d53409e0be43dbf5d0cf7ba0fcbc170e2117f6a1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745820"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly 方法
建立`Assembly`結構指定的組件包含中繼資料，並傳回相關聯的中繼資料語彙基元。  
  
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
 [in]如果不具備強式名稱組件識別的組件或 NULL 發行者公開金鑰。  
  
 `cbPublicKey`  
 [in]以位元組為單位的大小`pbPublicKey`。  
  
 `uHashAlgId`  
 [in]用來加密組件或 NULL，指定 sha-1 演算法中的檔案雜湊演算法的識別項。  
  
 `szName`  
 [in]組件的人類看得懂的文字名稱。 此值不得超過 1024年個字元。  
  
 `pMetaData`  
 [in]ASSEMBLYMETADATA 執行個體，其中包含組件的版本、 平台，以及地區設定資訊的指標。  
  
 `dwAssemblyFlags`  
 [in]組合[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值，描述組件的功能。  
  
 `pmda`  
 [out]中繼資料語彙基元指標。  
  
## <a name="remarks"></a>備註  
 只有一個`Assembly`中繼資料結構可以定義資訊清單內。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
