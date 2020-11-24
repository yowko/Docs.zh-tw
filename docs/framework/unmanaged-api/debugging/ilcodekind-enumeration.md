---
title: ILCodeKind 列舉
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: 7e9cf760ec609786804a05177349ee2eacd79eaf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692237"
---
# <a name="ilcodekind-enumeration"></a>ILCodeKind 列舉

[.NET Framework 4.5.2 與更新版本提供支援]  
  
 提供值，指定偵錯工具是否能夠存取分析工具 ReJIT 檢測中加入的區域變數或程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a>成員  
  
|成員名稱|描述|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|偵錯工具無權存取 ReJIT 檢測的資訊。|  
|`ILCODE_REJIT_IL`|偵錯工具有權存取 ReJIT 檢測的資訊。|  
  
## <a name="remarks"></a>備註  

 列舉的成員 `ILCodeKind` 可以傳遞至 [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) 和 [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) 方法，以判斷偵錯工具是否可以存取在 profiler ReJIT 檢測中加入的變數，以及至 [GetCodeEx](icordebugilframe4-getcodeex-method.md) 方法來判斷偵錯工具是否可以存取已檢測的 IL。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](debugging-enumerations.md)
- [ICorDebugILFrame4 介面](icordebugilframe4-interface.md)
- [ReJIT： How-To 指南](/archive/blogs/davbr/rejit-a-how-to-guide)
