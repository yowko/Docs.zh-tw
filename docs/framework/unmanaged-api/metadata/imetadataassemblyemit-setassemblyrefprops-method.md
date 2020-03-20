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
ms.openlocfilehash: 6ad6bbb8a4c69f575bbeba3a297c46e049a97325
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176041"
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
 [在]指定要修改的`AssemblyRef`元資料結構的中繼資料權杖。  
  
 `pbPublicKeyOrToken`  
 [在]引用程式集的發行者的公共金鑰。  
  
 `cbPublicKeyOrToken`  
 [在]的大小（以位元組為單位）。 `pbPublicKeyOrToken`  
  
 `szName`  
 [在]程式集的人類可讀文本名稱。  
  
 `pMetaData`  
 [在]指向 ASSEMBLYMETADATA 實例的指標，其中包含程式集的版本、平臺和地區設定資訊。  
  
 `pbHashValue`  
 [在]指向與程式集關聯的雜湊資料的指標。  
  
 `cbHashValue`  
 [在]的大小（以位元組為單位）。 `pbHashValue`  
  
 `dwAssemblyRefFlags`  
 [在]指定引用程式集屬性的[程式集 RefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)值的位組合。  
  
## <a name="remarks"></a>備註  
 要創建`AssemblyRef`元資料結構，請使用[IMetaDataAssemblyEmit：:DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
