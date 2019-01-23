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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7452b76509d5eca592cc3b95df1f77703ec1111
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561825"
---
# <a name="corilmap-structure"></a>COR_IL_MAP 結構
指定函式相關位移中的變更。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`oldOffset`|舊 Microsoft intermediate language (MSIL) 位移相對於函式的開頭。|  
|`newOffset`|新的 MSIL 位移相對於函式的開頭。|  
|`fAccurate`|`true` 如果對應已知為正確;否則， `false`。|  
  
## <a name="remarks"></a>備註  
 對應的格式如下所示：偵錯工具會假設`oldOffset`指原始、 未修改 MSIL 程式碼中的 MSIL 位移。 `newOffset`參數會參考新的已檢測的程式碼中對應的 MSIL 位移。  
  
 逐步執行才能正常運作，應該符合下列需求：  
  
-   此對應應該以遞增順序排序。  
  
-   已檢測的 MSIL 程式碼應該不會重新排列。  
  
-   原始的 MSIL 程式碼應該不會移除。  
  
-   對應應該包含對應用程式資料庫 (PDB) 檔案中的所有序列點的項目。  
  
 對應不會插補遺漏的項目。 下列範例會顯示對應和它的結果。  
  
 對應：  
  
-   0 的舊位移、 0 的新位移  
  
-   5 的舊位移、 10 個新的位移  
  
-   9 的舊位移、 20 的新位移  
  
 結果：  
  
-   0、 1、 2、 3 或 4 的舊位移會對應至新的位移為 0。  
  
-   5、 6、 7 或 8 的舊位移會對應至 10 的新位移。  
  
-   9 或更新版本的舊位移會對應至新的位移 20。  
  
-   0、 1、 2、 3、 4、 5、 6、 7、 8 或 9 新位移會對應至舊的位移 0。  
  
-   新的位移，10、 11、 12、 13、 14、 15、 16、 17、 18 或 19 的會對應至舊位移 5。  
  
-   20 或更高版本的新位移會對應至舊位移 9。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorProf.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
