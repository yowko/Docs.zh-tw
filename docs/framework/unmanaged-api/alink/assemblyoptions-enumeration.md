---
title: AssemblyOptions 列舉
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 49e7b73559e8def890f8df8f596fbe8ad5bb5d3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777476"
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions 列舉
列舉元件選項。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a>欄位  
  
|欄位|描述|  
|-----------|-----------------|  
|optAssemTitle|String-表示元件標題。|  
|optAssemDescription|String-包含元件描述。|  
|optAssemConfig|String-包含元件設定。|  
|optAssemOS|字串編碼為： "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion"。|  
|optAssemProcessor|ULONG|  
|optAssemLocale|String-包含元件地區設定。|  
|optAssemVersion|字串編碼為：「主要. 次要. 組建修訂」。|  
|optAssemCompany|String-包含公司。|  
|optAssemProduct|String-包含產品名稱。|  
|optAssemProductVersion|String （也稱為 InformationalVersion）。|  
|optAssemCopyright|String-包含著作權資訊。|  
|optAssemTrademark|String-包含商標資訊。|  
|optAssemKeyFile|字串（檔案名）。|  
|optAssemKeyName|字串（索引鍵名稱）。|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool （也稱為 DelaySign）。|  
|optAssemFileVersion|字串編碼為「主要. 次要. 組建修訂版」--與 ProductVersion 相同。|  
|optAssemSatelliteVer|字串編碼為「主要. 次要. 組建. 修訂」。|  
|optLastAssemOption|元素數目的計數器。|  
  
## <a name="requirements"></a>需求  
 **標頭：** alink。h  
  
 連結**庫**： alink .dll  
  
## <a name="see-also"></a>另請參閱

- [Al.exe (組件連結器)](../../tools/al-exe-assembly-linker.md)
