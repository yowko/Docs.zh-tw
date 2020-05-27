---
title: IMetaDataAssemblyEmit::SetFileProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
ms.openlocfilehash: 9990daea1b097532de53684921d3f10c520a3b1a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008062"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a>IMetaDataAssemblyEmit::SetFileProps 方法
修改指定的 `File` 中繼資料結構。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `file`  
 在元資料標記，指定 `File` 要修改的元資料結構。  
  
 `pbHashValue`  
 在與檔案相關聯之雜湊資料的指標。  
  
 `cbHashValue`  
 在的大小（以位元組為單位） `pbHashValue` 。  
  
 `dwFileFlags`  
 在[CorFileFlags](corfileflags-enumeration.md)值的位元組合，這個組合會指定檔案的各種屬性。  
  
## <a name="remarks"></a>備註  
 若要建立 `File` 元資料結構，請使用[IMetaDataAssemblyEmit：:D efinefile](imetadataassemblyemit-definefile-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
