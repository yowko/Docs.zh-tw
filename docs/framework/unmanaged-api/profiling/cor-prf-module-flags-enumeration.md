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
ms.openlocfilehash: 7d9e187d4aede772b7a002359cd3bdd350aaec77
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682142"
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
  
|member|描述|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|模組已從磁片載入。|  
|COR_PRF_MODULE_NGEN|模組是由原生映射產生器 ( # A0) 所產生。|  
|COR_PRF_MODULE_DYNAMIC|模組是由命名空間中的方法所建立 <xref:System.Reflection.Emit?displayProperty=nameWithType> 。|  
|COR_PRF_MODULE_COLLECTIBLE|模組的存留期是由垃圾收集行程所管理。|  
|COR_PRF_MODULE_RESOURCE|模組不包含任何中繼資料，而且會嚴格地當做資源使用。 此位的 managed 對等專案是 <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> 方法。|  
|COR_PRF_MODULE_FLAT_LAYOUT|模組在記憶體中的版面配置是平坦的，未對應。 如果模組已設定此位，則在處理標頭中 (Rva) 的相對虛擬位址時，直接從可攜式可執行檔 (PE) 檔案標頭中讀取資訊的分析工具將必須特別小心。|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|此模組元件的中繼資料中會設定 Windows 執行階段內容類型旗標。 這是所有 Windows 中繼資料 ( winmd) 模組的情況。|  
  
## <a name="remarks"></a>備註  

 COR_PRF_MODULE_FLAGS 的位會在 `pdwModuleFlags` [ICorProfilerInfo3：： GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md) 方法的 output 參數中傳回給 profiler。 有兩個或多個旗標的組合是可行的，但並非所有組合都可行。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析列舉](profiling-enumerations.md)
