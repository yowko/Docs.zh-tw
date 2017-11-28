---
title: "IMetaDataAssemblyEmit::DefineAssemblyRef 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssemblyRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 074e589b84e21de4ec3bcc3c54a865297587d383
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
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
  
#### <a name="parameters"></a>參數  
 `pbPublicKeyOrToken`  
 [in]參考的組件的 「 發行者 」 的公開金鑰。 Helper 函式[StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)可以用來取得要做為此參數傳遞的公開金鑰的雜湊。  
  
 `cbPublicKeyOrToken`  
 [in]以位元組為單位的大小`pbPublicKeyOrToken`。  
  
 `szName`  
 [in]人類看得懂的文字之組件的名稱。 此值不能超過 1024年個字元。  
  
 `pMetaData`  
 [in]ASSEMBLYMETADATA 執行個體，其中包含參考的組件的版本、 平台和地區設定資訊。  
  
 `pbHashValue`  
 [in]雜湊相關聯的資料與參考的組件。 選擇項。  
  
 `cbHashValue`  
 [in]以位元組為單位的大小`pbHashValue`。  
  
 `dwAssemblyRefFlags`  
 [in]位元組合[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)影響行為的執行引擎的值。  
  
 `pmdar`  
 [out]所傳回的指標`AssemblyRef`中繼資料語彙基元。  
  
## <a name="remarks"></a>備註  
 一個`AssemblyRef`必須定義這個組件參考的每個組件的中繼資料結構。  
  
 執行階段參考組件的詳細資料會傳遞至組件解析程式，其中指出它們代表 「 建立 」 時的資訊。 組件解析程式接著會套用原則。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
