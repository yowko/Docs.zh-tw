---
title: IMetaDataImport::GetPinvokeMap 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
ms.openlocfilehash: c34215f48190e60bd1a851f31b8b23f09491f4e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729235"
---
# <a name="imetadataimportgetpinvokemap-method"></a>IMetaDataImport::GetPinvokeMap 方法

取得 ModuleRef 語彙基元以代表 PInvoke 呼叫的目標組件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a>參數  

 `tk`  
 在要取得其 PInvoke 對應中繼資料的 FieldDef 或 MethodDef 標記。  
  
 `pdwMappingFlags`  
 擴展用於對應之旗標的指標。 這個值是 [CorPinvokeMap](corpinvokemap-enumeration.md) 列舉的位元遮罩。  
  
 `szImportName`  
 擴展非受控目標 DLL 的名稱。  
  
 `cchImportName`  
 在的大小（以寬字元為單位） `szImportName` 。  
  
 `pchImportName`  
 擴展傳回的寬字元數 `szImportName` 。  
  
 `pmrImportDLL`  
 擴展ModuleRef token 的指標，代表未受管理的目標物件程式庫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
