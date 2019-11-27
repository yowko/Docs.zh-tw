---
title: IMetaDataTables 介面
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
ms.openlocfilehash: 17305f2c088dd6f479da4c823d3db0fd50c0b3d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443228"
---
# <a name="imetadatatables-interface"></a>IMetaDataTables 介面
提供儲存和擷取資料表中的中繼資料資訊的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetBlob 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|取得位於指定之資料行索引處之二進位大型物件（BLOB）的指標。|  
|[GetBlobHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|取得 BLOB 堆積的大小（以位元組為單位）。|  
|[GetCodedTokenInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|取得與指定之資料列索引相關聯之標記陣列的指標。|  
|[GetColumn 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|取得指定之資料表索引的資料表中，位於指定之資料行索引之資料行中的值指標。|  
|[GetColumnInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|取得指定資料表中指定之資料行的相關資料。|  
|[GetGuid 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|從指定索引處的資料列取得 GUID。|  
|[GetGuidHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|取得 GUID 堆積的大小（以位元組為單位）。|  
|[GetNextBlob 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|取得資料表中下一個 BLOB 的索引。|  
|[GetNextGuid 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|取得目前資料表資料行中下一個 GUID 值的索引。|  
|[GetNextString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|取得目前資料表資料行中下一個字串的索引。|  
|[GetNextUserString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|取得包含目前資料表資料行中下一個硬式編碼字串的資料列索引。|  
|[GetNumTables 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|取得目前 `IMetaDataTables` 實例範圍中的資料表數目。|  
|[GetRow 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|在指定之資料表索引的資料表中，取得位於指定資料列索引處的資料列。|  
|[GetString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|從目前參考範圍的資料表資料行中，取得位於指定索引位置的字串。|  
|[GetStringHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|取得字串堆積的大小（以位元組為單位）。|  
|[GetTableIndex 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|取得指定之標記所參考之資料表的索引。|  
|[GetTableInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|取得指定資料表索引處之資料表的名稱、資料列大小、資料列數目、資料行數目和索引鍵資料行索引。|  
|[GetUserString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|取得在目前範圍的字串資料行中指定索引處的硬式編碼字串。|  
|[GetUserStringHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|取得使用者字串堆積的大小（以位元組為單位）。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataTables2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
