---
title: IMetaDataTables::GetGuid 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 6f273cb03ad00957afb2bd78fe538a940fae236a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501231"
---
# <a name="imetadatatablesgetguid-method"></a>IMetaDataTables::GetGuid 方法
從指定索引處的資料列取得 GUID。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a>參數  
 `ixGuid`  
 在要從中取得 GUID 的資料列索引。  
  
 `ppGuid`  
 脫銷GUID 指標的指標。  
  
## <a name="remarks"></a>備註  

  我們不建議使用這個方法，因為它不會傳回一致的結果。 如需 GUID 資料表的詳細資訊，請參閱通用語言基礎結構（CLI）檔，特別是「分割區 II：元資料定義和語法」。 檔可從線上取得;請參閱[ECMA c # 和通用語言基礎結構標準](../../../standard/components.md#applicable-standards)和[標準 ecma-335-通用語言基礎結構（CLI）](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataTables 介面](imetadatatables-interface.md)
- [IMetaDataTables2 介面](imetadatatables2-interface.md)
