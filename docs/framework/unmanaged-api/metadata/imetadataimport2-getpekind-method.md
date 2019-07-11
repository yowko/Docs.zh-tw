---
title: IMetaDataImport2::GetPEKind 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91c80566ed284403ad559583a1e4f1025eb09985
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755325"
---
# <a name="imetadataimport2getpekind-method"></a>IMetaDataImport2::GetPEKind 方法
取得值，識別性質之可攜式執行檔 (PE) 中的程式碼檔，通常是 DLL 或 EXE 檔案，定義目前的中繼資料範圍內。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a>參數  
 `pdwPEKind`  
 [out]值的指標[CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)描述的 PE 檔的列舉型別。  
  
 `pdwMachine`  
 [out]識別電腦架構值的指標。 請參閱下一節，如需可能值。  
  
## <a name="remarks"></a>備註  
 所參考的值`pdwMachine`參數可以是下列其中之一。  
  
|值|電腦架構|  
|-----------|--------------------------|  
|IMAGE_FILE_MACHINE_I386<br /><br /> 0x014C|x86|  
|IMAGE_FILE_MACHINE_IA64<br /><br /> 0x0200|Intel IPF|  
|IMAGE_FILE_MACHINE_AMD64<br /><br /> 0x8664|X64|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [CorPEKind 列舉](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
