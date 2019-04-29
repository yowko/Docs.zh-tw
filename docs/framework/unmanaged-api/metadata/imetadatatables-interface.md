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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b2298e2d67e8a50e11d53d864f0e78f3b549e45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645173"
---
# <a name="imetadatatables-interface"></a>IMetaDataTables 介面
提供儲存和擷取資料表中的中繼資料資訊的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetBlob 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|取得二進位大型物件 (BLOB) 的指標，在指定的資料行索引。|  
|[GetBlobHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|取得大小，以位元組為單位，對 BLOB 堆積。|  
|[GetCodedTokenInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|取得與指定的資料列索引相關聯的語彙基元的陣列指標。|  
|[GetColumn 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|取得指定的資料行索引，在指定的資料表索引的資料表中的資料行中包含的值的指標。|  
|[GetColumnInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|取得指定的資料表中指定的資料行的相關的資料。|  
|[GetGuid 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|從指定索引處的資料列中取得的 GUID。|  
|[GetGuidHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|取得大小，以位元組為單位，GUID 堆積。|  
|[GetNextBlob 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|取得資料表中的下一個 BLOB 的索引。|  
|[GetNextGuid 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|取得目前的資料表資料行中的下一個 GUID 值的索引。|  
|[GetNextString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|取得目前的資料表資料行中的下一個字串的索引。|  
|[GetNextUserString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|取得包含目前的資料表資料行中的下一步 硬式編碼字串的資料列索引。|  
|[GetNumTables 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|取得目前的範圍中的資料表數目`IMetaDataTables`執行個體。|  
|[GetRow 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|取得指定的資料列索引，在指定的資料表索引的資料表中的資料列。|  
|[GetString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|取得字串的指定索引處與資料表資料行中目前參考的範圍。|  
|[GetStringHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|取得大小，以位元組為單位對字串堆積。|  
|[GetTableIndex 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|取得指定語彙基元所參考之資料表的索引。|  
|[GetTableInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|取得在指定的資料表索引的名稱、 資料列大小、 資料列數目、 資料行和資料表的索引鍵資料行索引。|  
|[GetUserString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|取得在目前範圍中的字串資料行中的指定索引處的硬式編碼的字串。|  
|[GetUserStringHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|取得大小，以位元組為單位的使用者字串堆積。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataTables2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
