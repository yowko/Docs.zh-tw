---
title: CorDebugEHClause 結構
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40820a805310786eeb0effd7c5284c1a70a6e70b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407596"
---
# <a name="cordebugehclause-structure"></a>CorDebugEHClause 結構
[在 .NET Framework 4.5.2 及更新版本中支援]  
  
 代表中繼語言 (IL) 程式碼給定片段的例外狀況處理 (EH) 子句。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`Flags`|描述 EH 子句中之例外狀況資訊的位元欄位。 如需詳細資訊，請參閱＜備註＞一節。|  
|`TryOffset`|`try` 區塊從方法主體開頭位移的位元組數。|  
|`TryLength`|`try` 區塊的長度 (位元組)。|  
|`HandlerOffset`|此 `try` 區塊之處理常式的位置。|  
|`HandlerLength`|處理常式程式碼的大小 (位元組)。|  
|`ClassToken`|以類型為基礎之例外狀況處理常式的中繼資料 Token。|  
|`FilterOffset`|以篩選器為基礎之例外狀況處理常式自方法主體開頭位移的位元組數。|  
  
## <a name="remarks"></a>備註  
 陣列`CoreDebugEHClause`值由[GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)方法。  
  
 EH 子句資訊以 CLI 規格定義。 如需詳細資訊，請參閱[標準 ecma-355： 通用語言基礎結構 (CLI)，第 6 版](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。  
  
 `flags` 欄位可以包含下列旗標。 請注意，CorDebug.idl 或 CorDebug.h 中並未定義這些旗標。  
  
|旗標|值|描述|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|0x00000000|宣告類型的例外狀況子句。|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|0x00000001|例外狀況篩選器與處理常式子句。|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|0x00000002|`finally` 子句。|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|0x00000004|錯誤子句 (`finally` 子句只會在擲出例外狀況時呼叫)。|  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [GetEHClauses 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)  
 [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
