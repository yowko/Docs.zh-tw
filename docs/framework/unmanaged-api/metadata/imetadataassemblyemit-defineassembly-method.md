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
ms.openlocfilehash: 6d783e27c60db7381025f3b2382728e3996323ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725725"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly 方法

建立 `Assembly` 包含指定元件之中繼資料的結構，並傳回相關聯的元資料標記。  
  
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
 在識別元件發行者的公開金鑰; 如果元件不是強式名稱，則為 Null。  
  
 `cbPublicKey`  
 在的大小（以位元組為單位） `pbPublicKey` 。  
  
 `uHashAlgId`  
 在用來加密元件中之檔案的雜湊演算法識別碼，或 Null 以指定 SHA-1 演算法。  
  
 `szName`  
 在元件的人們可讀取文字名稱。 此值不得超過1024個字元。  
  
 `pMetaData`  
 在ASSEMBLYMETADATA 實例的指標，其中包含元件的版本、平臺和地區設定資訊。  
  
 `dwAssemblyFlags`  
 在描述元件功能的 [CorAssemblyFlags](corassemblyflags-enumeration.md) 值組合。  
  
 `pmda`  
 擴展元資料標記的指標。  
  
## <a name="remarks"></a>備註  

 只有一個 `Assembly` 元資料結構可以在資訊清單中定義。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
