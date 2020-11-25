---
title: ICorDebugILFrame4 介面
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
ms.openlocfilehash: 7d0f3661c7941c5f2f85fa5b0b67af213de75f05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724945"
---
# <a name="icordebugilframe4-interface"></a>ICorDebugILFrame4 介面

[.NET Framework 4.5.2 與更新版本提供支援]  
  
 提供的方法可讓您在中繼語言 (IL) 程式碼的框架中，存取區域變數和程式碼。 參數可指定偵錯工具是否能夠存取在分析工具 ReJIT 檢測中加入的變數和程式碼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx 方法](icordebugilframe4-enumeratelocalvariablesex-method.md)|傳回目前框架中可用的區域變數清單。|  
|[GetCodeEx 方法](icordebugilframe4-getcodeex-method.md)|傳回此堆疊框架正在執行的程式碼。|  
|[GetLocalVariableEx 方法](icordebugilframe4-getlocalvariableex-method.md)|傳回 IL 框架中的區域變數值。|  
  
## <a name="remarks"></a>備註  

 這些方法除了提供 [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md)、 [GetCode](icordebugframe-getcode-method.md)和 [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) 方法所提供的功能之外，還提供了功能。 每個方法都包含 `flags` 參數，可指定是否顯示分析工具 ReJIT 要求所定義的區域變數或程式碼。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
