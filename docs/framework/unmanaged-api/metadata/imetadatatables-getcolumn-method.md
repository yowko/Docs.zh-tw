---
title: IMetaDataTables::GetColumn 方法
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 853f137d91e1b3eb4f3f65a06522618f8441dcb3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053681"
---
# <a name="imetadatatablesgetcolumn-method"></a>IMetaDataTables::GetColumn 方法
取得給定資料表中指定之資料行和資料列的儲存格所包含之值的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a>參數

 `ixTbl`  
 在資料表的索引。  
  
 `ixCol`  
 在資料表中資料行的索引。  
  
 `rid`  
 在資料表中的資料列索引。  
  
 `pVal`  
 脫銷儲存格中值的指標。  
 
## <a name="remarks"></a>備註

透過`pVal`傳回之值的 interpretion 取決於資料行的類型。 您可以藉由呼叫 IMetaDataTables 來判斷資料行類型。 [GetColumnInfo](imetadatatables-getcolumninfo-method.md)。

- **GetColumn**方法會自動將**Rid**或**CodedToken**類型的資料行轉換成完整 32 `mdToken`位的值。
- 它也會自動將8位或16位的值轉換成完整的32位值。 
- 若是*堆積*類型的資料行，傳回的*pVal*將會是對應堆積的索引。

| 資料行類型              | pVal 包含 | 註解                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>（0到63）  | mdToken     | *pVal*會包含完整的 Token。 函式會自動將 Rid 轉換成完整 token。 |
| `iCodedToken`..`iCodedTokenMax`<br>（64. 95） | mdToken | 傳回時， *pVal*會包含完整的 Token。 函式會自動將 CodedToken 解壓縮至完整 token。 |
| `iSHORT`（96）            | Int16         | 自動將簽章延伸至32位。  |
| `iUSHORT`（97）           | UInt16        | 自動將簽章延伸至32位。  |
| `iLONG`（98）             | Int32         |                                        | 
| `iULONG`（99）            | UInt32        |                                        |
| `iBYTE`（100）            | Byte          | 自動將簽章延伸至32位。  |
| `iSTRING`（101）          | 字串堆積索引 | *pVal*是字串堆積中的索引。 請使用[IMetadataTables：： GetString](imetadatatables-getstring-method.md)來取得實際的資料行字串值。 |
| `iGUID`（102）            | Guid 堆積索引 | *pVal*是 Guid 堆積中的索引。 請使用[IMetadataTables：： GetGuid](imetadatatables-getguid-method.md)來取得實際的資料行 Guid 值。 |
| `iBLOB`（103）            | Blob 堆積索引 | *pVal*是 Blob 堆積中的索引。 請使用[IMetadataTables：： GetBlob](imetadatatables-getblob-method.md)來取得實際的資料行 Blob 值。 |
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 **LIBRARY:** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataTables 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
