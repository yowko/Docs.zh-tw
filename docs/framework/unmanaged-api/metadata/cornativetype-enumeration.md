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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf62000fd4ec5c8f3dea3fa7d560b3f9ead33fa7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045458"
---
# <a name="cornativetype-enumeration"></a>CorNativeType 列舉
包含值，這些值描述原生 Unmanaged 類型。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
|成員|描述|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|已過時。|  
|`NATIVE_TYPE_VOID`|已過時。|  
|`NATIVE_TYPE_BOOLEAN`|4 位元組的布林值，其中 TRUE 且非零，則為 FALSE 會是零。|  
|`NATIVE_TYPE_I1`|帶正負號的 8 位元整數值。|  
|`NATIVE_TYPE_U1`|不帶正負號的 8 位元整數值。|  
|`NATIVE_TYPE_I2`|帶正負號的 16 位元整數值。|  
|`NATIVE_TYPE_U2`|不帶正負號的 16 位元整數值。|  
|`NATIVE_TYPE_I4`|帶正負號的 32 位元整數值。|  
|`NATIVE_TYPE_U4`|32 位元不帶正負號的整數值。|  
|`NATIVE_TYPE_I8`|帶正負號的 64 位元整數值。|  
|`NATIVE_TYPE_U8`|不帶正負號的 64 位元整數值。|  
|`NATIVE_TYPE_R4`|4 位元組浮點數值。|  
|`NATIVE_TYPE_R8`|8 位元組浮點數值。|  
|`NATIVE_TYPE_SYSCHAR`|已過時。|  
|`NATIVE_TYPE_VARIANT`|已過時。|  
|`NATIVE_TYPE_CURRENCY`|數字的 COM 型別對應至 managed<xref:System.Decimal>型別。|  
|`NATIVE_TYPE_PTR`|已過時。|  
|`NATIVE_TYPE_DECIMAL`|已過時。|  
|`NATIVE_TYPE_DATE`|已過時。|  
|`NATIVE_TYPE_BSTR`|COM Interop。|  
|`NATIVE_TYPE_LPSTR`|LPSTR 的字串值。|  
|`NATIVE_TYPE_LPWSTR`|LPWSTR 的字串值。|  
|`NATIVE_TYPE_LPTSTR`|LPTSTR 的字串值。|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|固定的系統定義的字串值。|  
|`NATIVE_TYPE_OBJECTREF`|已過時。|  
|`NATIVE_TYPE_IUNKNOWN`|COM Interop。|  
|`NATIVE_TYPE_IDISPATCH`|COM Interop。|  
|`NATIVE_TYPE_STRUCT`|原生結構的值。|  
|`NATIVE_TYPE_INTF`|COM Interop。|  
|`NATIVE_TYPE_SAFEARRAY`|COM Interop。|  
|`NATIVE_TYPE_FIXEDARRAY`|固定長度的陣列值。|  
|`NATIVE_TYPE_INT`|原生的 16 位元帶正負號的整數值。|  
|`NATIVE_TYPE_UINT`|原生的 16 位元不帶正負號的整數值。|  
|`NATIVE_TYPE_NESTEDSTRUCT`|已過時。<br /><br /> 使用 NATIVE_TYPE_STRUCT。|  
|`NATIVE_TYPE_BYVALSTR`|COM Interop。|  
|`NATIVE_TYPE_ANSIBSTR`|COM Interop。|  
|`NATIVE_TYPE_TBSTR`|COM Interop。<br /><br /> 選取 BSTR 或 ANSIBSTR 視平台。|  
|`NATIVE_TYPE_VARIANTBOOL`|2 位元組的布林值，其中為 true，則為-1，而 FALSE 是零。|  
|`NATIVE_TYPE_FUNC`|函式指標。|  
|`NATIVE_TYPE_ASANY`|任何原生型別的參考。|  
|`NATIVE_TYPE_ARRAY`|未指定類型的成員與陣列的參考。|  
|`NATIVE_TYPE_LPSTRUCT`|結構的 32 位元的整數指標。|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|自訂封送處理器的原生型別。<br /><br /> 這必須遵循下列格式的字串來：「 原生型別名稱/0Custom 封送處理器型別名稱/0Optional cookie/0"或"{原生輸入 GUID} / 0Custom 封送處理器輸入 cookie 的名稱/0Optional/0 」|  
|`NATIVE_TYPE_ERROR`|COM Interop。<br /><br /> ELEMENT_TYPE_I4 與此類型會對應至 VT_HRESULT。|  
|`NATIVE_TYPE_IINSPECTABLE`|原生`IInspectable`型別。|  
|`NATIVE_TYPE_HSTRING`|原生`HString`。|  
|`NATIVE_TYPE_MAX`|無效的值。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
