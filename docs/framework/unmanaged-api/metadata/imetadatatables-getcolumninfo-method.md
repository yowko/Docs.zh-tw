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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd67d9faafedf4fb92c69618d4464ebb2ce47dcc
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774251"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo 方法
取得指定資料表中指定之資料行的相關資料。  
  
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
 在所需資料表的索引。  
  
 `ixCol`  
 在所需資料行的索引。  
  
 `poCol`  
 脫銷資料列中資料行位移的指標。  
  
 `pcbCol`  
 脫銷資料行大小的指標，以位元組為單位。  
  
 `pType`  
 脫銷資料行中數值型別的指標。  
  
 `ppName`  
 脫銷指向資料行名稱之指標的指標。  
 
## <a name="remarks"></a>備註

傳回的資料行類型落在值的範圍內：

| pType                    | 描述   | Helper 函式                   |
|--------------------------|---------------|-----------------------------------|
| `0`。`iRidMax`<br>（0到63）   | 掉           | **IsRidType**<br>**IsRidOrToken** |
| `iCodedToken`。`iCodedTokenMax`<br>（64. 95） | 程式碼標記 | **IsCodedTokenType** <br>**IsRidOrToken** |
| `iSHORT` （96）            | Int16         | **IsFixedType**                   |
| `iUSHORT` （97）           | UInt16        | **IsFixedType**                   |
| `iLONG` （98）             | Int32         | **IsFixedType**                   |
| `iULONG` （99）            | UInt32        | **IsFixedType**                   |
| `iBYTE` （100）            | Byte          | **IsFixedType**                   |
| `iSTRING` （101）          | String        | **IsHeapType**                    |
| `iGUID` （102）            | GUID          | **IsHeapType**                    |
| `iBLOB` （103）            | Blob          | **IsHeapType**                    |

您可以使用下列方式來讀取儲存在*堆積*中的值（也就是 `IsHeapType == true`）：

- `iSTRING`： **IMetadataTables. GetString**
- `iGUID`： **IMetadataTables. GetGUID**
- `iBLOB`： **IMetadataTables. GetBlob**

> [!IMPORTANT]
> 若要使用上表中所定義的常數，請包含*cor*標頭檔所提供的指示詞 `#define _DEFINE_META_DATA_META_CONSTANTS`。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IMetaDataTables 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
