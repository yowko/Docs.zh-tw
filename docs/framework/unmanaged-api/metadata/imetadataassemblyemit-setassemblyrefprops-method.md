---
title: "IMetaDataAssemblyEmit::SetAssemblyRefProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 84b6c0d748578b717a128ff3b808977ba902c6dc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps 方法
修改指定的 `AssemblyRef` 中繼資料結構。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,   
    [in] const ASSEMBLYMETADATA     *pMetaData,   
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ar`  
 [in]指定的中繼資料語彙基元`AssemblyRef`要修改的中繼資料結構。  
  
 `pbPublicKeyOrToken`  
 [in]參考的組件的 「 發行者 」 的公開金鑰。  
  
 `cbPublicKeyOrToken`  
 [in]以位元組為單位的大小`pbPublicKeyOrToken`。  
  
 `szName`  
 [in]人類看得懂的文字之組件的名稱。  
  
 `pMetaData`  
 [in]ASSEMBLYMETADATA 執行個體，其中包含組件的版本、 平台，以及地區設定資訊指標。  
  
 `pbHashValue`  
 [in]與組件相關聯的雜湊資料指標。  
  
 `cbHashValue`  
 [in]以位元組為單位的大小`pbHashValue`。  
  
 `dwAssemblyRefFlags`  
 [in]位元組合[AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)指定參考組件屬性的值。  
  
## <a name="remarks"></a>備註  
 若要建立`AssemblyRef`中繼資料結構，使用[imetadataassemblyemit:: Defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
