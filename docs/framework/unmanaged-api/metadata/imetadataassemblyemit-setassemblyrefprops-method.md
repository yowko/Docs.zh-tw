---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: fb381a872cbeb787da0c6920f2cdeef434fb33ea
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008088"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps 方法
修改指定的 `AssemblyRef` 中繼資料結構。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
## <a name="parameters"></a>參數  
 `ar`  
 在元資料標記，指定 `AssemblyRef` 要修改的元資料結構。  
  
 `pbPublicKeyOrToken`  
 在所參考元件之發行者的公開金鑰。  
  
 `cbPublicKeyOrToken`  
 在的大小（以位元組為單位） `pbPublicKeyOrToken` 。  
  
 `szName`  
 在元件的人類看得懂的文字名稱。  
  
 `pMetaData`  
 在ASSEMBLYMETADATA 實例的指標，其中包含元件的版本、平臺和地區設定資訊。  
  
 `pbHashValue`  
 在與元件相關聯之雜湊資料的指標。  
  
 `cbHashValue`  
 在的大小（以位元組為單位） `pbHashValue` 。  
  
 `dwAssemblyRefFlags`  
 在[AssemblyRefFlags](assemblyrefflags-enumeration.md)值的位元組合，這個組合會指定參考元件的屬性。  
  
## <a name="remarks"></a>備註  
 若要建立 `AssemblyRef` 元資料結構，請使用[IMetaDataAssemblyEmit：:D efineassemblyref](imetadataassemblyemit-defineassemblyref-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
