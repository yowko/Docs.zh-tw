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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37d91ca7935e114504864683075f4809de7270fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599110"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyProps 方法
修改指定的 `Assembly` 中繼資料結構。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `pma`  
 [in]指定中繼資料語彙基元`Assembly`要修改的中繼資料結構。  
  
 `pbPublicKey`  
 [in]組件的 「 發行者 」 的公開的索引鍵的指標。  
  
 `cbPublicKey`  
 [in]以位元組為單位的大小`pbPublicKey`。  
  
 `ulHashAlgId`  
 [in]用來雜湊的組件檔案的雜湊演算法識別項。  
  
 `szName`  
 [in]組件的人類看得懂的文字名稱。  
  
 `pMetaData`  
 [in]包含組件的版本、 平台，以及地區設定資訊 ASSEMBLYMETADATA 指標。  
  
 `dwAssemblyFlags`  
 [in]位元組合[AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)指定組件的各種屬性的值。  
  
## <a name="remarks"></a>備註  
 若要建立`Assembly`中繼資料結構，使用[imetadataassemblyemit:: Defineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
