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
ms.openlocfilehash: 48617022940d889abedb9a9d25f04782371c4a5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451941"
---
# <a name="corprfmoduleflags-enumeration"></a>COR_PRF_MODULE_FLAGS 列舉
指定模組的屬性。  
  
## <a name="syntax"></a>語法  
  
```  
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
|COR_PRF_MODULE_DISK|從磁碟載入模組。|  
|COR_PRF_MODULE_NGEN|此模組是由原生映像產生器 (Ngen.exe) 產生。|  
|COR_PRF_MODULE_DYNAMIC|中的方法所建立的模組<xref:System.Reflection.Emit?displayProperty=nameWithType>命名空間。|  
|COR_PRF_MODULE_COLLECTIBLE|模組的存留期會由記憶體回收行程所管理。|  
|COR_PRF_MODULE_RESOURCE|此模組包含沒有中繼資料，並嚴格來做為資源。 此位元的 managed 對應項會<xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType>方法。|  
|COR_PRF_MODULE_FLAT_LAYOUT|在記憶體中模組的版面配置是一般，未對應。 如果模組有設定此位元，閱讀資訊直接從可攜式執行檔 (PE) 標頭會解譯相對虛擬位址 (Rva) 標頭中的時務必謹慎的分析工具。|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|此模組的組件中的中繼資料中設有 Windows 執行階段內容的型別旗標。 這是所有的 Windows 中繼資料 (.winmd) 模組的情況。|  
  
## <a name="remarks"></a>備註  
 COR_PRF_MODULE_FLAGS 位元會傳回給分析工具在`pdwModuleFlags`輸出參數的[icorprofilerinfo3:: Getmoduleinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)方法。 兩個或多個旗標的某些組合可能會但並非所有的組合都有可能。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
