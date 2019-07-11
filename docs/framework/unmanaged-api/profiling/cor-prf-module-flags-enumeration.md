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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f94867db6908f0999604511d9782b6f5abfb5e77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752042"
---
# <a name="corprfmoduleflags-enumeration"></a>COR_PRF_MODULE_FLAGS 列舉
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
  
|成員|描述|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|從磁碟載入的模組。|  
|COR_PRF_MODULE_NGEN|模組產生的原生映像產生器 (Ngen.exe)。|  
|COR_PRF_MODULE_DYNAMIC|中的方法所建立的模組<xref:System.Reflection.Emit?displayProperty=nameWithType>命名空間。|  
|COR_PRF_MODULE_COLLECTIBLE|模組的存留期會受記憶體回收行程。|  
|COR_PRF_MODULE_RESOURCE|此模組會包含任何中繼資料，並會用於為資源。 此位元的 managed 對等是<xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType>方法。|  
|COR_PRF_MODULE_FLAT_LAYOUT|在記憶體中模組的版面配置是扁平的未對應。 如果模組有設定此位元，閱讀資訊，直接從可攜式執行檔 (PE) 檔案標頭會解譯相對虛擬位址 (Rva) 標頭中的時務必謹慎的分析工具。|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Windows 執行階段內容的型別旗標是設定此模組的組件中繼資料中。 這是 Windows 中繼資料 (.winmd) 的所有模組的情況。|  
  
## <a name="remarks"></a>備註  
 中的分析工具會傳回從 COR_PRF_MODULE_FLAGS 的位元`pdwModuleFlags`輸出參數[ICorProfilerInfo3::GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)方法。 兩個或多個旗標的某些組合可能會但並非所有組合都都有可能。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
