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
ms.openlocfilehash: 5ae4c5743b01c4a9087323678d315473631cb32f
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274043"
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
  
|成員|描述|  
|------------|-----------------|  
|`oldOffset`|相對於函數開頭的舊 Microsoft 中繼語言（MSIL）位移。|  
|`newOffset`|相對於函數開頭的新 MSIL 位移。|  
|`fAccurate`|`true`如果已知對應是正確的，則為，否則為`false`。|  
  
## <a name="remarks"></a>備註  
 對應的格式如下所示：偵錯工具會假設， `oldOffset`這是指原始、未修改的 msil 程式碼內的 MSIL 位移。 `newOffset`參數會參考新檢測的程式碼內對應的 MSIL 位移。  
  
 若要讓逐步執行正常運作，應符合下列需求：  
  
- 對應應該以遞增順序排序。  
  
- 不應將已檢測的 MSIL 程式碼重新排序。  
  
- 不應該移除原始的 MSIL 程式碼。  
  
- 對應應該包含專案，以對應程式資料庫（PDB）檔案中的所有序列點。  
  
 對應不會插補遺漏的專案。 下列範例會顯示地圖和其結果。  
  
 地圖  
  
- 0個舊位移，0個新位移  
  
- 5個舊位移，10個新位移  
  
- 9個舊的位移，20個新的位移  
  
 更  
  
- 舊的位移為0、1、2、3或4，將會對應至新的位移0。  
  
- 舊的位移5、6、7或8會對應到新的位移10。  
  
- 舊的位移9或更高版本會對應到新的位移20。  
  
- 新的位移為0、1、2、3、4、5、6、7、8或9，將會對應到舊的位移0。  
  
- 10、11、12、13、14、15、16、17、18或19的新位移會對應到舊的位移5。  
  
- 新的位移20或以上會對應到舊的位移9。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl，Corprof.idl .idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
