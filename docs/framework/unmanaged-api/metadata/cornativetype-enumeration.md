---
title: CorNativeType 列舉
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
ms.openlocfilehash: 95bbb0cc2f223cfa96e1314ed28f46016c81a2fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687693"
---
# <a name="cornativetype-enumeration"></a>CorNativeType 列舉

包含值，這些值描述原生 Unmanaged 類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|已過時。|  
|`NATIVE_TYPE_VOID`|已過時。|  
|`NATIVE_TYPE_BOOLEAN`|4位元組布林值，其中 TRUE 為非零，而 FALSE 為零。|  
|`NATIVE_TYPE_I1`|帶正負號的8位整數值。|  
|`NATIVE_TYPE_U1`|不帶正負號的8位整數值。|  
|`NATIVE_TYPE_I2`|帶正負號的16位整數值。|  
|`NATIVE_TYPE_U2`|不帶正負號的16位整數值。|  
|`NATIVE_TYPE_I4`|帶正負號的 32 位元整數值。|  
|`NATIVE_TYPE_U4`|32 位元不帶正負號的整數值。|  
|`NATIVE_TYPE_I8`|帶正負號的64位整數值。|  
|`NATIVE_TYPE_U8`|不帶正負號的64位整數值。|  
|`NATIVE_TYPE_R4`|4位元組浮點數數值。|  
|`NATIVE_TYPE_R8`|8位元組浮點數數值。|  
|`NATIVE_TYPE_SYSCHAR`|已過時。|  
|`NATIVE_TYPE_VARIANT`|已過時。|  
|`NATIVE_TYPE_CURRENCY`|對應于 managed 類型的數值 COM 類型 <xref:System.Decimal> 。|  
|`NATIVE_TYPE_PTR`|已過時。|  
|`NATIVE_TYPE_DECIMAL`|已過時。|  
|`NATIVE_TYPE_DATE`|已過時。|  
|`NATIVE_TYPE_BSTR`|COM Interop。|  
|`NATIVE_TYPE_LPSTR`|LPSTR 的字串值。|  
|`NATIVE_TYPE_LPWSTR`|LPWSTR 的字串值。|  
|`NATIVE_TYPE_LPTSTR`|LPTSTR 的字串值。|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|固定的系統定義字串值。|  
|`NATIVE_TYPE_OBJECTREF`|已過時。|  
|`NATIVE_TYPE_IUNKNOWN`|COM Interop。|  
|`NATIVE_TYPE_IDISPATCH`|COM Interop。|  
|`NATIVE_TYPE_STRUCT`|原生結構值。|  
|`NATIVE_TYPE_INTF`|COM Interop。|  
|`NATIVE_TYPE_SAFEARRAY`|COM Interop。|  
|`NATIVE_TYPE_FIXEDARRAY`|固定長度的陣列值。|  
|`NATIVE_TYPE_INT`|原生16位帶正負號的整數值。|  
|`NATIVE_TYPE_UINT`|原生16位不帶正負號的整數值。|  
|`NATIVE_TYPE_NESTEDSTRUCT`|已過時。<br /><br /> 使用 NATIVE_TYPE_STRUCT。|  
|`NATIVE_TYPE_BYVALSTR`|COM Interop。|  
|`NATIVE_TYPE_ANSIBSTR`|COM Interop。|  
|`NATIVE_TYPE_TBSTR`|COM Interop。<br /><br /> 視平臺而定，選取 BSTR 或 ANSIBSTR。|  
|`NATIVE_TYPE_VARIANTBOOL`|2位元組布林值，其中 TRUE 為-1，而 FALSE 為零。|  
|`NATIVE_TYPE_FUNC`|函式指標。|  
|`NATIVE_TYPE_ASANY`|任何原生類型的參考。|  
|`NATIVE_TYPE_ARRAY`|具有未指定類型之成員的陣列參考。|  
|`NATIVE_TYPE_LPSTRUCT`|結構的32位整數指標。|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|自訂封送處理器原生類型。<br /><br /> 其後必須接著下列格式的字串： "Native type name/0Custom 封送處理器 type name/0Optional cookie/0" 或 "{Native type GUID}/0Custom 封送處理器類型名稱/0Optional cookie/0"|  
|`NATIVE_TYPE_ERROR`|COM Interop。<br /><br /> 使用 ELEMENT_TYPE_I4 此型別會對應到 VT_HRESULT。|  
|`NATIVE_TYPE_IINSPECTABLE`|原生 `IInspectable` 類型。|  
|`NATIVE_TYPE_HSTRING`|原生 `HString` 。|  
|`NATIVE_TYPE_MAX`|無效的值。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [中繼資料列舉](metadata-enumerations.md)
