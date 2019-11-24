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
|[GetBlob 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Gets a pointer to the binary large object (BLOB) at the specified column index.|  
|[GetBlobHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|Gets the size, in bytes, of the BLOB heap.|  
|[GetCodedTokenInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Gets a pointer to an array of tokens associated with the specified row index.|  
|[GetColumn 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.|  
|[GetColumnInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Gets data about the specified column in the specified table.|  
|[GetGuid 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Gets a GUID from the row at the specified index.|  
|[GetGuidHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|Gets the size, in bytes, of the GUID heap.|  
|[GetNextBlob 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Gets the index of the next BLOB in the table.|  
|[GetNextGuid 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Gets the index of the next GUID value in the current table column.|  
|[GetNextString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Gets the index of the next string in the current table column.|  
|[GetNextUserString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Gets the index of the row that contains the next hard-coded string in the current table column.|  
|[GetNumTables 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Gets the number of tables in the scope of the current `IMetaDataTables` instance.|  
|[GetRow 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Gets the row at the specified row index, in the table at the specified table index.|  
|[GetString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Gets the string at the specified index from the table column in the current reference scope.|  
|[GetStringHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Gets the size, in bytes, of the string heap.|  
|[GetTableIndex 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Gets the index for the table referenced by the specified token.|  
|[GetTableInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.|  
|[GetUserString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Gets the hard-coded string at the specified index in the string column in the current scope.|  
|[GetUserStringHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Gets the size, in bytes, of the user string heap.|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataTables2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
