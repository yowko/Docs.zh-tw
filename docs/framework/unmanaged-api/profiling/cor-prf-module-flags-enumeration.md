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
ms.openlocfilehash: 0f6fb469aa9d6d40b762bfd2feec28c28299732f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867109"
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|模組已從磁片載入。|  
|COR_PRF_MODULE_NGEN|模組是由原生映射產生器（Ngen.exe）所產生。|  
|COR_PRF_MODULE_DYNAMIC|模組是由 <xref:System.Reflection.Emit?displayProperty=nameWithType> 命名空間中的方法所建立。|  
|COR_PRF_MODULE_COLLECTIBLE|模組的存留期是由垃圾收集行程所管理。|  
|COR_PRF_MODULE_RESOURCE|此模組不包含任何中繼資料，而且會以嚴格的方式用來作為資源。 這個位的 managed 對等是 <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> 方法。|  
|COR_PRF_MODULE_FLAT_LAYOUT|模組在記憶體中的配置是平面的，不會對應。 如果模組已設定此位，則在解讀標頭中的相對虛擬位址（Rva）時，直接從可移植執行檔（PE）檔案標頭讀取資訊的分析工具必須謹慎。|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|此模組元件的中繼資料中會設定 Windows 執行階段內容類型旗標。 這是所有 Windows 中繼資料（winmd）模組的情況。|  
  
## <a name="remarks"></a>備註  
 COR_PRF_MODULE_FLAGS 中的位會傳回至[ICorProfilerInfo3：： GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md)方法之 `pdwModuleFlags` 輸出參數中的分析工具。 有兩個或多個旗標的組合是可行的，但並非所有組合都可行。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析列舉](profiling-enumerations.md)
