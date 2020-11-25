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
ms.openlocfilehash: 352e1acd1fdd8297754e18b2e8c6448ea723a557
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717025"
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions 列舉

列舉元件選項。  
  
## <a name="syntax"></a>Syntax  
  
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
|optAssemTitle|字串-表示元件標題。|  
|optAssemDescription|字串-包含元件描述。|  
|optAssemConfig|字串-包含元件設定。|  
|optAssemOS|字串編碼為： "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion"。|  
|optAssemProcessor|ULONG|  
|optAssemLocale|字串-包含元件地區設定。|  
|optAssemVersion|以字串編碼的： "主要。|  
|optAssemCompany|包含公司的字串。|  
|optAssemProduct|字串-包含產品名稱。|  
|optAssemProductVersion|字串 (也稱為 InformationalVersion) 。|  
|optAssemCopyright|字串-包含著作權資訊。|  
|optAssemTrademark|字串-包含商標資訊。|  
|optAssemKeyFile|字串 (的檔案名) 。|  
|optAssemKeyName| (索引鍵名稱) 的字串。|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (也稱為 DelaySign) 。|  
|optAssemFileVersion|字串編碼為 "主要... a.. a.. a.. a.. a.. a... a|  
|optAssemSatelliteVer|以字串編碼為 "主要。|  
|optLastAssemOption|元素數目的計數器。|  
  
## <a name="requirements"></a>需求  

 **標頭：** alink。h  
  
 連結 **庫**： alink.dll  
  
## <a name="see-also"></a>另請參閱

- [Al.exe (元件連結器) ](../../tools/al-exe-assembly-linker.md)
