---
title: GUID_ManagedName 屬性
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f14d00f17a61576a50e26d3cbcf734a10ed3c03a
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895012"
---
# <a name="guid_managedname-attribute"></a>GUID_ManagedName 屬性
定義自訂介面屬性，指定元件物件模型（COM）程式庫的 managed 命名空間名稱。  
  
## <a name="syntax"></a>語法  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a>參數  
 `value`  
 程式庫的受控命名空間名稱。  
  
## <a name="definition"></a>定義  
 `GUID_ManagedName`定義于 Cor 中，如下所示：  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>備註  
 自訂介面屬性會定義類型程式庫中物件的中繼資料。  
  
 使用<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> 或<xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> ，從屬性中取出受控名稱。  
  
 如需詳細資訊，請參閱 Visual C++ reference 檔中的[介面屬性](/cpp/windows/attributes/interface-attributes)。  
  
## <a name="example"></a>範例  
 下列範例顯示使用`GUID_ManagedName`屬性的程式庫定義。  
  
```idl
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** Cor。h
