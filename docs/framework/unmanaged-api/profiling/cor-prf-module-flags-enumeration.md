---
title: COR_PRF_MODULE_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_MODULE_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MODULE_FLAGS
helpviewer_keywords:
- COR_PRF_MODULE_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 7bc3a938-0df1-4739-9ff1-89cff454b704
topic_type:
- apiref
ms.openlocfilehash: 12e7faa8d9fee7698de9d9734f522d818f225c84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500815"
---
# <a name="cor_prf_module_flags-enumeration"></a>COR_PRF_MODULE_FLAGS 列舉
指定模組的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum  
{  
    COR_PRF_MODULE_DISK             = 0x00000001,  
    COR_PRF_MODULE_NGEN             = 0x00000002,  
    COR_PRF_MODULE_DYNAMIC          = 0x00000004,  
    COR_PRF_MODULE_COLLECTIBLE      = 0x00000008,  
    COR_PRF_MODULE_RESOURCE         = 0x00000010,  
    COR_PRF_MODULE_FLAT_LAYOUT      = 0x00000020,  
    COR_PRF_MODULE_WINDOWS_RUNTIME  = 0x00000040  
}   COR_PRF_MODULE_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|模組已從磁片載入。|  
|COR_PRF_MODULE_NGEN|模組是由原生映射產生器（Ngen.exe）所產生。|  
|COR_PRF_MODULE_DYNAMIC|模組是由命名空間中的方法所建立 <xref:System.Reflection.Emit?displayProperty=nameWithType> 。|  
|COR_PRF_MODULE_COLLECTIBLE|模組的存留期是由垃圾收集行程所管理。|  
|COR_PRF_MODULE_RESOURCE|此模組不包含任何中繼資料，而且會以嚴格的方式用來作為資源。 這個位的受控對等是 <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> 方法。|  
|COR_PRF_MODULE_FLAT_LAYOUT|模組在記憶體中的配置是平面的，不會對應。 如果模組已設定此位，則在解讀標頭中的相對虛擬位址（Rva）時，直接從可移植執行檔（PE）檔案標頭讀取資訊的分析工具必須謹慎。|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|此模組元件的中繼資料中會設定 Windows 執行階段內容類型旗標。 這是所有 Windows 中繼資料（winmd）模組的情況。|  
  
## <a name="remarks"></a>備註  
 COR_PRF_MODULE_FLAGS 中的位會傳回至 `pdwModuleFlags` [ICorProfilerInfo3：： GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md)方法之 output 參數中的分析工具。 有兩個或多個旗標的組合是可行的，但並非所有組合都可行。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析列舉](profiling-enumerations.md)
