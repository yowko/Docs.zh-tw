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
ms.openlocfilehash: 57df124f15f78daad053d9634e1baa969a65cc35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175274"
---
# <a name="imetadatatablesgetguid-method"></a>IMetaDataTables::GetGuid 方法
從指定索引處的行獲取 GUID。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a>參數  
 `ixGuid`  
 [在]要從中獲取 GUID 的行的索引。  
  
 `ppGuid`  
 [出]指向 GUID 的指標。  
  
## <a name="remarks"></a>備註  

  我們不建議使用此方法，因為它不返回一致的結果。 有關 GUID 表的資訊，請參閱通用語言基礎結構 （CLI） 文檔，尤其是"分區 II：元資料定義和語義"。 文檔可線上獲取;請參閱[ECMA C# 和通用語言基礎結構標準和](../../../standard/components.md#applicable-standards)[標準 ECMA-335 - 通用語言基礎結構 （CLI）。](http://www.ecma-international.org/publications/standards/Ecma-335.htm)  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataTables 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
