---
title: IMetaDataAssemblyEmit::DefineAssemblyRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e480c408c10eb9e135f260426750f7747e5d8ce5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117348"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>IMetaDataAssemblyEmit::DefineAssemblyRef 方法
為這個組件所參考的組件，建立包含其中繼資料的 `AssemblyRef` 結構，並且傳回關聯的中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbPublicKeyOrToken`  
 [in]參考的組件的 「 發行者 」 的公開金鑰。 Helper 函式[StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)可用來取得的公用金鑰來作為此參數傳遞的雜湊。  
  
 `cbPublicKeyOrToken`  
 [in]以位元組為單位的大小`pbPublicKeyOrToken`。  
  
 `szName`  
 [in]組件的人類看得懂的文字名稱。 此值不得超過 1024年個字元。  
  
 `pMetaData`  
 [in]ASSEMBLYMETADATA 執行個體，其中包含參考的組件的版本、 平台和地區設定資訊。  
  
 `pbHashValue`  
 [in]雜湊相關聯的資料與參考的組件。 選擇性。  
  
 `cbHashValue`  
 [in]以位元組為單位的大小`pbHashValue`。  
  
 `dwAssemblyRefFlags`  
 [in]位元組合[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)影響行為的執行引擎的值。  
  
 `pmdar`  
 [out]所傳回的指標`AssemblyRef`中繼資料語彙基元。  
  
## <a name="remarks"></a>備註  
 一個`AssemblyRef`必須定義這個組件參考的每個組件的中繼資料結構。  
  
 在執行階段，參考的組件的詳細資料會傳遞至組件解析程式，並指出它們代表的"as 建置 」 的資訊。 組件解析程式接著會套用原則。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
