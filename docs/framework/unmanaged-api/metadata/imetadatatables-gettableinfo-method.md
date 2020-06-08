---
title: IMetaDataTables::GetTableInfo 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
ms.openlocfilehash: 7e60dd9535809ca13f3bbe6ac76f5ea1209df734
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501160"
---
# <a name="imetadatatablesgettableinfo-method"></a>IMetaDataTables::GetTableInfo 方法
取得指定資料表的名稱、資料列大小、資料列數目、資料行數目和索引鍵資料行索引。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a>參數  
 `ixTbl`  
 在要傳回其屬性之資料表的識別碼。  
  
 `pcbRow`  
 脫銷資料表資料列大小（以位元組為單位）的指標。  
  
 `pcRows`  
 脫銷資料表中的資料列數目指標。  
  
 `pcCols`  
 脫銷資料表中的資料行數目指標。  
  
 `piKey`  
 脫銷索引鍵資料行之索引的指標，如果資料表沒有索引鍵資料行，則為-1。  
  
 `ppName`  
 脫銷指向資料表名稱之指標的指標。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataTables 介面](imetadatatables-interface.md)
- [IMetaDataTables2 介面](imetadatatables2-interface.md)
