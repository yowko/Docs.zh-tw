---
title: IMetaDataAssemblyEmit::DefineFile 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: cabd6a47e5d6fc2a4cea87b16d349d9c778b3507
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176054"
---
# <a name="imetadataassemblyemitdefinefile-method"></a>IMetaDataAssemblyEmit::DefineFile 方法
為這個組件所參考的組件，建立包含其中繼資料的 `File` 中繼資料結構，並且傳回關聯的中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a>參數  
 `szName`  
 [在]要使用的檔的名稱。  
  
 `pbHashValue`  
 [在]指向與程式集關聯的雜湊資料的指標。  
  
 `cbHashValue`  
 [在]的大小（以位元組為單位）。 `pbHashValue`  
  
 `dwFileFlags`  
 [在]指定屬性設置的值的`FileFlags`位組合。  
  
 `pmdf`  
 [出]指向返回`File`的權杖的指標。  
  
## <a name="remarks"></a>備註  
 必須`File`為生成此程式集時屬於此程式集的每個檔定義一個元資料結構，不包括包含中繼資料的檔。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
