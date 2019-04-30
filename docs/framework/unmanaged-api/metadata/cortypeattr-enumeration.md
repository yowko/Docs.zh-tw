---
title: CorTypeAttr 列舉
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43e7c973ee22350f26b4f86bcc8b4c4c727291ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045184"
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr 列舉
包含值，這些值表示類型中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`tdVisibilityMask`|用於型別可視性資訊。|  
|`tdNotPublic`|指定的型別不是公用的範圍中。|  
|`tdPublic`|指定的類型是公用的範圍中。|  
|`tdNestedPublic`|指定的類型巢狀具有公用可視性。|  
|`tdNestedPrivate`|指定的類型巢狀使用私用可見度。|  
|`tdNestedFamily`|指定的型別使用家族可視性的巢狀。|  
|`tdNestedAssembly`|指定的型別使用巢狀組件可見性。|  
|`tdNestedFamANDAssem`|指定的型別使用家族和組件的可見性的巢狀。|  
|`tdNestedFamORAssem`|指定的型別使用家族或組件的可見性的巢狀。|  
|`tdLayoutMask`|取得類型的配置資訊。|  
|`tdAutoLayout`|指定此類型的欄位會自動配置。|  
|`tdSequentialLayout`|指定此類型的欄位會以循序方式配置。|  
|`tdExplicitLayout`|指定明確提供該欄位的配置。|  
|`tdClassSemanticsMask`|取得型別的相關語意資訊。|  
|`tdClass`|指定此類型為類別。|  
|`tdInterface`|指定此類型為介面。|  
|`tdAbstract`|指定此類型為抽象。|  
|`tdSealed`|指定的型別不能擴充。|  
|`tdSpecialName`|指定特殊的類別名稱。 其名稱將告訴您如何。|  
|`tdImport`|指定的型別會匯入。|  
|`tdSerializable`|指定的型別是可序列化。|  
|`tdWindowsRuntime`|指定此類型為[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。|  
|`tdStringFormatMask`|取得字串編碼和格式化的方式的相關資訊。|  
|`tdAnsiClass`|指定此類型會解譯為 ANSI LPTSTR。|  
|`tdUnicodeClass`|指定此類型會解譯為 Unicode LPTSTR。|  
|`tdAutoClass`|指定此類型會自動解譯 LPTSTR。|  
|`tdCustomFormatClass`|指定該類型具有非標準的編碼，依照`CustomFormatMask`。|  
|`tdCustomFormatMask`|您可以使用此遮罩來取得原生 interop 的非標準編碼資訊。 未指定這些兩位元值的意義。|  
|`tdBeforeFieldInit`|指定第一次嘗試存取的靜態欄位之前，必須先初始化型別。|  
|`tdForwarder`|指定，將匯出的類型，以及類型轉送子。|  
|`tdReservedMask`|這個旗標和下方的旗標，則會由 common language runtime 內部使用。|  
|`tdRTSpecialName`|指定 common language runtime 應該檢查名稱編碼方式。|  
|`tdHasSecurity`|指定該類型具有與其相關聯的安全性。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
