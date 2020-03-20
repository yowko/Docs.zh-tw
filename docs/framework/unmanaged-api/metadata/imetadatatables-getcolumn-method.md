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
ms.openlocfilehash: f43d4d1547cbe92f325950e1697dada83b42c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177131"
---
# <a name="imetadatatablesgetcolumn-method"></a>IMetaDataTables::GetColumn 方法
獲取指向給定表中指定列和行儲存格中包含的值的指標。  
  
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
 [在]表的索引。  
  
 `ixCol`  
 [在]表中列的索引。  
  
 `rid`  
 [在]表中行的索引。  
  
 `pVal`  
 [出]指向儲存格中值的指標。  

## <a name="remarks"></a>備註

返回的值的解釋`pVal`取決於列的類型。 可以通過調用[IMetaDataTables](imetadatatables-getcolumninfo-method.md)來確定列類型。

- **GetColumn**方法會自動將 **"Rid"** 或"**編碼權杖"** 類型的列轉換為完整的 32 位`mdToken`值。
- 它還會自動將 8 位或 16 位值轉換為完整的 32 位值。
- 對於*堆*類型列，返回的*pVal*將是相應堆中的索引。

| 資料行類型              | pVal 包含 | 註解                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)  | mdToken     | *pVal*將包含一個完整的權杖。 該函數會自動將 Rid 轉換為完整權杖。 |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | mdToken | 返回後 *，pVal*將包含一個完整的權杖。 該函數會自動將編碼權杖解壓縮為完整權杖。 |
| `iSHORT`(96)            | Int16         | 自動簽名擴展到 32 位。  |
| `iUSHORT`(97)           | UInt16        | 自動簽名擴展到 32 位。  |
| `iLONG`(98)             | Int32         |                                        |
| `iULONG`(99)            | UInt32        |                                        |
| `iBYTE`(100)            | Byte          | 自動簽名擴展到 32 位。  |
| `iSTRING`(101)          | 字串堆索引 | *pVal*是字串堆中的索引。 使用[IMetadataTables：：獲取String](imetadatatables-getstring-method.md)獲取實際列字串值。 |
| `iGUID`(102)            | 吉德堆索引 | *pVal*是 Guid 堆中的索引。 使用[IMetadataTables：：getGuid](imetadatatables-getguid-method.md)獲取實際列 Guid 值。 |
| `iBLOB`(103)            | Blob 堆索引 | *pVal*是 Blob 堆中的索引。 使用[IMetadataTables：：獲取 Blob](imetadatatables-getblob-method.md)獲取實際列 Blob 值。 |
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataTables 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
