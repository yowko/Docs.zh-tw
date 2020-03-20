---
title: IMetaDataTables::GetColumnInfo 方法
ms.date: 10/10/2019
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
ms.openlocfilehash: cc8aac32149fed952737d928e16a8f6efc448c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177127"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo 方法
獲取有關指定表中指定列的資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetColumnInfo (
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a>參數
=======

 `ixTbl`  
 [在]所需表的索引。  
  
 `ixCol`  
 [在]所需列的索引。  
  
 `poCol`  
 [出]指向行中列偏移的指標。  
  
 `pcbCol`  
 [出]指向列的大小（以位元組為單位）的指標。  
  
 `pType`  
 [出]指向列中數值型別的指標。  
  
 `ppName`  
 [出]指向列名稱的指標。  

## <a name="remarks"></a>備註

返回的列類型在值範圍內：

| p類型                    | 描述   | 説明器功能                   |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)   | 擺脫           | **IsRidType**<br>**IsRidorToken** |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | 編碼權杖 | **已編碼權杖類型** <br>**IsRidorToken** |
| `iSHORT`(96)            | Int16         | **固定類型**                   |
| `iUSHORT`(97)           | UInt16        | **固定類型**                   |
| `iLONG`(98)             | Int32         | **固定類型**                   |
| `iULONG`(99)            | UInt32        | **固定類型**                   |
| `iBYTE`(100)            | Byte          | **固定類型**                   |
| `iSTRING`(101)          | String        | **IsHeap 類型**                    |
| `iGUID`(102)            | Guid          | **IsHeap 類型**                    |
| `iBLOB`(103)            | Blob          | **IsHeap 類型**                    |

可以使用以下方式讀取堆中存儲*的值（即* `IsHeapType == true`），

- `iSTRING`**：IMetadatatables.GetString**
- `iGUID`**：IMetadatatables.GetGUID**
- `iBLOB`**：IMetadatatables.獲取Blob**

> [!IMPORTANT]
> 要使用上表中定義的常量，請包括`#define _DEFINE_META_DATA_META_CONSTANTS`*cor.h*標標頭檔提供的指令。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataTables 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
