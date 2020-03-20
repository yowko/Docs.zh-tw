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
ms.openlocfilehash: 14bd352099890e4ca36321d550b8e982d4373231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177893"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly 方法
創建包含`Assembly`指定組件中繼資料的結構並返回關聯的中繼資料權杖。  
  
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
 [在]標識程式集的發行者的公共金鑰，如果程式集未強命名，則為 Null。  
  
 `cbPublicKey`  
 [在]的大小（以位元組為單位）。 `pbPublicKey`  
  
 `uHashAlgId`  
 [在]用於加密程式集中的檔的雜湊演算法的識別碼，或用於指定 SHA-1 演算法的 Null。  
  
 `szName`  
 [在]程式集的人類可讀文本名稱。 此值不得超過 1024 個字元。  
  
 `pMetaData`  
 [在]指向 ASSEMBLYMETADATA 實例的指標，其中包含程式集的版本、平臺和地區設定資訊。  
  
 `dwAssemblyFlags`  
 [在]描述程式集功能的[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值的組合。  
  
 `pmda`  
 [出]指向中繼資料權杖的指標。  
  
## <a name="remarks"></a>備註  
 只能在清單`Assembly`中定義一個元資料結構。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
