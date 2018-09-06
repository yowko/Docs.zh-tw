---
title: IMetaDataTables::GetTableIndex 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableIndex
helpviewer_keywords:
- GetTableIndex method [.NET Framework metadata]
- IMetaDataTables::GetTableIndex method [.NET Framework metadata]
ms.assetid: c6ec3800-e0d9-4387-afb8-ddc0b818114c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f86fd424b397859dd70e113f2d8b8dcae7226f53
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041063"
---
# <a name="imetadatatablesgettableindex-method"></a>IMetaDataTables::GetTableIndex 方法
取得指定語彙基元所參考之資料表的索引。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
#### <a name="parameters"></a>參數  
 `token`  
 [in]參考資料表的語彙基元。  
  
 `pixTbl`  
 [out]傳回的索引所參考之資料表的指標。  
  
## <a name="remarks"></a>備註  
 我們不建議使用這個方法，因為它不會傳回一致的結果。 如需詳細資訊 GUID 表格，Common Language Infrastructure (CLI) 文件，尤其是"Partition II:: 中繼資料定義和語意 >。 您可以線上取得這份文件；請參閱 MSDN 上的 [ECMA C# 和通用語言基礎結構標準](https://go.microsoft.com/fwlink/?LinkID=99212)，以及 Ecma International 網站上的[標準 ECMA-335 - 通用語言基礎結構 (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataTables 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [IMetaDataTables2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
