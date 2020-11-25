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
ms.openlocfilehash: d335beecc12e0c1c895e42888ad7172f78062ff7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702533"
---
# <a name="imetadataimport2getpekind-method"></a>IMetaDataImport2::GetPEKind 方法

取得值，這個值可識別在目前的中繼資料範圍中定義的可攜性可執行檔 (PE) 檔（通常是 DLL 或 EXE 檔案）中程式碼的本質。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a>參數  

 `pdwPEKind`  
 擴展描述 PE 檔之 [CorPEKind](corpekind-enumeration.md) 列舉值的指標。  
  
 `pdwMachine`  
 擴展值的指標，可識別電腦的架構。 請參閱下一節以取得可能的值。  
  
## <a name="remarks"></a>備註  

 參數所參考的值 `pdwMachine` 可以是下列其中一項。  
  
|值|電腦架構|  
|-----------|--------------------------|  
|IMAGE_FILE_MACHINE_I386<br /><br /> 0x014C|x86|  
|IMAGE_FILE_MACHINE_IA64<br /><br /> 0x0200|Intel IPF|  
|IMAGE_FILE_MACHINE_AMD64<br /><br /> 0x8664|x64|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport2 介面](imetadataimport2-interface.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
- [CorPEKind 列舉](corpekind-enumeration.md)
