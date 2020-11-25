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
ms.openlocfilehash: 50ce4e5e6125eae493bb62032d5c6bd8887c1afb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699088"
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr 列舉

包含值，這些值表示類型中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
|member|描述|  
|------------|-----------------|  
|`tdVisibilityMask`|用於類型可見度資訊。|  
|`tdNotPublic`|指定類型不在公用範圍中。|  
|`tdPublic`|指定類型在公用範圍中。|  
|`tdNestedPublic`|指定類型是以公用可見度進行嵌套。|  
|`tdNestedPrivate`|指定以私用可見度來巢狀型別。|  
|`tdNestedFamily`|指定類型會以家族可見度進行嵌套。|  
|`tdNestedAssembly`|指定類型會以元件可見度進行嵌套。|  
|`tdNestedFamANDAssem`|指定類型會以家族和元件可見度進行嵌套。|  
|`tdNestedFamORAssem`|指定類型會以家族或元件可見度進行嵌套。|  
|`tdLayoutMask`|取得類型的版面配置資訊。|  
|`tdAutoLayout`|指定此類型的欄位會自動設定。|  
|`tdSequentialLayout`|指定將此類型的欄位依序排列。|  
|`tdExplicitLayout`|指定明確提供欄位版面配置。|  
|`tdClassSemanticsMask`|取得類型的相關語義資訊。|  
|`tdClass`|指定此類型為類別。|  
|`tdInterface`|指定此類型為介面。|  
|`tdAbstract`|指定此類型為抽象。|  
|`tdSealed`|指定無法擴充類型。|  
|`tdSpecialName`|指定類別名稱是特殊的。 其名稱會描述做法。|  
|`tdImport`|指定要匯入的類型。|  
|`tdSerializable`|指定類型為可序列化。|  
|`tdWindowsRuntime`|指定這個型別是 Windows 執行階段型別。|  
|`tdStringFormatMask`|取得如何編碼和格式化字串的相關資訊。|  
|`tdAnsiClass`|指定此類型將 LPTSTR 解讀為 ANSI。|  
|`tdUnicodeClass`|指定此類型將 LPTSTR 解讀為 Unicode。|  
|`tdAutoClass`|指定此型別會自動解讀 LPTSTR。|  
|`tdCustomFormatClass`|指定類型具有非標準編碼，如所指定 `CustomFormatMask` 。|  
|`tdCustomFormatMask`|使用這個遮罩來取得原生 interop 的非標準編碼資訊。 未指定這兩個位值的意義。|  
|`tdBeforeFieldInit`|指定必須在第一次嘗試存取靜態欄位之前初始化型別。|  
|`tdForwarder`|指定匯出類型和類型轉寄站。|  
|`tdReservedMask`|通用語言執行時間會在內部使用此旗標和下列旗標。|  
|`tdRTSpecialName`|指定通用語言執行時間應該檢查名稱編碼。|  
|`tdHasSecurity`|指定類型具有與其相關聯的安全性。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
