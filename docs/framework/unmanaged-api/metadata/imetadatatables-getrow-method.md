---
title: IMetaDataTables::GetRow 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177109"
---
# <a name="imetadatatablesgetrow-method"></a>IMetaDataTables::GetRow 方法
在指定的表索引的表中獲取指定行索引處的行。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a>參數  
 `ixTbl`  
 [在]將從中檢索行的表的索引。  
  
 `rid`  
 [在]要獲取的行的索引。  
  
 `ppRow`  
 [出]指向行的指標。  
  
## <a name="remarks"></a>備註  

  我們不建議使用此方法，因為它不返回一致的結果。 有關 GUID 表的資訊，請參閱通用語言基礎結構 （CLI） 文檔，尤其是"分區 II：元資料定義和語義"。 文檔可線上獲取;請參閱[ECMA C# 和通用語言基礎結構標準和](../../../standard/components.md#applicable-standards)[標準 ECMA-335 - 通用語言基礎結構 （CLI）。](http://www.ecma-international.org/publications/standards/Ecma-335.htm)  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataTables 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
