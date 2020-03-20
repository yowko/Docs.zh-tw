---
title: COR_IL_MAP 結構
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
ms.openlocfilehash: 4c79d0e4e37f3f884651e49c8fff6db72fac4f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179298"
---
# <a name="cor_il_map-structure"></a>COR_IL_MAP 結構
指定函式相關位移中的變更。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`oldOffset`|舊的 Microsoft 中間語言 （MSIL） 相對於函數的開頭偏移。|  
|`newOffset`|新的 MSIL 相對於函數的開頭偏移。|  
|`fAccurate`|`true`如果已知映射準確;如果映射準確;否則， `false`.|  
  
## <a name="remarks"></a>備註  
 地圖的格式如下：調試器將假定引用`oldOffset`原始未修改的 MSIL 代碼中的 MSIL 偏移量。 該`newOffset`參數是指新檢測代碼中的相應 MSIL 偏移量。  
  
 為了正常工作，應滿足以下要求：  
  
- 地圖應按昇冪排序。  
  
- 不應重新排序已檢測的 MSIL 代碼。  
  
- 不應刪除原始 MSIL 代碼。  
  
- 地圖應包括用於對應程式資料庫 （PDB） 檔中的所有序列點的條目。  
  
 地圖不會插值缺少的條目。 下面的示例顯示地圖及其結果。  
  
 地圖：  
  
- 0 舊偏移，0 新偏移  
  
- 5 個舊偏移，10 個新偏移  
  
- 9 個舊偏移，20 個新偏移  
  
 結果：  
  
- 舊偏移 0、1、2、3 或 4 將映射到新的偏移量 0。  
  
- 舊偏移 5、6、7 或 8 將映射到新的偏移量 10。  
  
- 舊偏移量為 9 或更高，將映射到新的偏移量 20。  
  
- 新的偏移量為 0、1、2、3、4、5、6、7、8 或 9 將映射到舊偏移 0。  
  
- 10、11、12、13、14、15、16、17、18 或 19 的新偏移將映射到舊偏移 5。  
  
- 新的偏移量為 20 或更高，將映射到舊偏移 9。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** 科爾科調試.idl， 科爾普羅芬.伊德爾  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
