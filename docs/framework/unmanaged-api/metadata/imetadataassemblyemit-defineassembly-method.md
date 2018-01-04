---
title: "IMetaDataAssemblyEmit::DefineAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35bc85cdc4380ee112b7095866c05e5d7639200b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly 方法
建立`Assembly`結構包含其中繼資料的指定組件，並傳回相關聯的中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `pbPublicKey`  
 [in]識別發行者的組件或為 NULL，如果組件不具備強式名稱公開金鑰。  
  
 `cbPublicKey`  
 [in]以位元組為單位的大小`pbPublicKey`。  
  
 `uHashAlgId`  
 [in]用來加密的檔案中的組件或為 NULL 來指定 sha-1 演算法的雜湊演算法識別項。  
  
 `szName`  
 [in]人類看得懂的文字之組件的名稱。 此值不能超過 1024年個字元。  
  
 `pMetaData`  
 [in]ASSEMBLYMETADATA 執行個體，其中包含組件的版本、 平台，以及地區設定資訊指標。  
  
 `dwAssemblyFlags`  
 [in]組合[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值描述組件的功能。  
  
 `pmda`  
 [out]中繼資料語彙基元的指標。  
  
## <a name="remarks"></a>備註  
 只有一個`Assembly`可以定義清單內的中繼資料結構。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
