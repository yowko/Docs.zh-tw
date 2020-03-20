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
ms.openlocfilehash: 09a351db65c7ed310d3eb68c71a5207ed6040dd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177975"
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
|`NATIVE_TYPE_BOOLEAN`|4 位元組布林值，其中 TRUE 為非零，FALSE 為零。|  
|`NATIVE_TYPE_I1`|已簽名的 8 位整數值。|  
|`NATIVE_TYPE_U1`|未簽名的 8 位整數值。|  
|`NATIVE_TYPE_I2`|已簽名的 16 位整數值。|  
|`NATIVE_TYPE_U2`|未簽名的 16 位整數值。|  
|`NATIVE_TYPE_I4`|帶正負號的 32 位元整數值。|  
|`NATIVE_TYPE_U4`|32 位元不帶正負號的整數值。|  
|`NATIVE_TYPE_I8`|已簽名的 64 位整數值。|  
|`NATIVE_TYPE_U8`|未簽名的 64 位整數值。|  
|`NATIVE_TYPE_R4`|4 位元組浮點數值。|  
|`NATIVE_TYPE_R8`|8 位元組浮點數值。|  
|`NATIVE_TYPE_SYSCHAR`|已過時。|  
|`NATIVE_TYPE_VARIANT`|已過時。|  
|`NATIVE_TYPE_CURRENCY`|對應于託管<xref:System.Decimal>類型的數位 COM 類型。|  
|`NATIVE_TYPE_PTR`|已過時。|  
|`NATIVE_TYPE_DECIMAL`|已過時。|  
|`NATIVE_TYPE_DATE`|已過時。|  
|`NATIVE_TYPE_BSTR`|COM Interop。|  
|`NATIVE_TYPE_LPSTR`|LPSTR 字串值。|  
|`NATIVE_TYPE_LPWSTR`|LPWSTR 字串值。|  
|`NATIVE_TYPE_LPTSTR`|LPTSTR 字串值。|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|固定的系統定義的字串值。|  
|`NATIVE_TYPE_OBJECTREF`|已過時。|  
|`NATIVE_TYPE_IUNKNOWN`|COM Interop。|  
|`NATIVE_TYPE_IDISPATCH`|COM Interop。|  
|`NATIVE_TYPE_STRUCT`|本機結構值。|  
|`NATIVE_TYPE_INTF`|COM Interop。|  
|`NATIVE_TYPE_SAFEARRAY`|COM Interop。|  
|`NATIVE_TYPE_FIXEDARRAY`|固定長度陣列值。|  
|`NATIVE_TYPE_INT`|本機 16 位簽名整數值。|  
|`NATIVE_TYPE_UINT`|本機 16 位不帶正負號的整數值。|  
|`NATIVE_TYPE_NESTEDSTRUCT`|已過時。<br /><br /> 使用NATIVE_TYPE_STRUCT。|  
|`NATIVE_TYPE_BYVALSTR`|COM Interop。|  
|`NATIVE_TYPE_ANSIBSTR`|COM Interop。|  
|`NATIVE_TYPE_TBSTR`|COM Interop。<br /><br /> 根據平臺選擇 BSTR 或 ANSIBSTR。|  
|`NATIVE_TYPE_VARIANTBOOL`|2 位元組布林值，其中 TRUE 為 -1，FALSE 為零。|  
|`NATIVE_TYPE_FUNC`|函式指標。|  
|`NATIVE_TYPE_ASANY`|對任何本機類型的引用。|  
|`NATIVE_TYPE_ARRAY`|對具有未指定類型成員的陣列的引用。|  
|`NATIVE_TYPE_LPSTRUCT`|指向結構的 32 位整數指標。|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|自訂封送器本機類型。<br /><br /> 之後必須使用以下格式的字串："本機類型名稱/0自訂封送器類型名稱/0可選 Cookie/0"或"{本機類型 GUID}/0自訂封送器類型名稱/0 可選 Cookie/0"|  
|`NATIVE_TYPE_ERROR`|COM Interop。<br /><br /> 使用ELEMENT_TYPE_I4此類型映射到VT_HRESULT。|  
|`NATIVE_TYPE_IINSPECTABLE`|本機`IInspectable`類型。|  
|`NATIVE_TYPE_HSTRING`|本機`HString`。|  
|`NATIVE_TYPE_MAX`|無效的值。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫德  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
