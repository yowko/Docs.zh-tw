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
ms.openlocfilehash: ba53ff30f0b6d0ae7fed7db422b7c0a242204a2c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689426"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>IMetaDataAssemblyEmit::DefineAssemblyRef 方法

為這個組件所參考的組件，建立包含其中繼資料的 `AssemblyRef` 結構，並且傳回關聯的中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 在參考之元件發行者的公開金鑰。 Helper 函式 [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) 可用來取得公開金鑰的雜湊，以做為此參數傳遞。  
  
 `cbPublicKeyOrToken`  
 在的大小（以位元組為單位） `pbPublicKeyOrToken` 。  
  
 `szName`  
 在元件的人們可讀取文字名稱。 此值不得超過1024個字元。  
  
 `pMetaData`  
 在ASSEMBLYMETADATA 實例，其中包含所參考元件的版本、平臺和地區設定資訊。  
  
 `pbHashValue`  
 在與參考元件相關聯的雜湊資料。 選擇性。  
  
 `cbHashValue`  
 在的大小（以位元組為單位） `pbHashValue` 。  
  
 `dwAssemblyRefFlags`  
 在 [CorAssemblyFlags](corassemblyflags-enumeration.md) 值的位元組合，這些值會影響執行引擎的行為。  
  
 `pmdar`  
 擴展傳回之 `AssemblyRef` 元資料標記的指標。  
  
## <a name="remarks"></a>備註  

 您 `AssemblyRef` 必須為這個元件所參考的每個元件定義一個元資料結構。  
  
 在執行時間，會將參考元件的詳細資料傳遞給元件解析程式，並指出它們代表「已建立」的資訊。 然後，元件解析程式會套用原則。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
