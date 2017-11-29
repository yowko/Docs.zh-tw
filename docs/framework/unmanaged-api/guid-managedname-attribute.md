---
title: "GUID_ManagedName 屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GUID_ManagedName
api_location: alink.dll
api_type: COM
f1_keywords: GUID_ManagedName
helpviewer_keywords: GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf0facaa1107fcc6dcd93cbf0252024dc6f73b0a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="guidmanagedname-attribute"></a>GUID_ManagedName 屬性
定義指定之元件物件模型 (COM) 程式庫的受管理的命名空間名稱的自訂介面屬性。  
  
## <a name="syntax"></a>語法  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
#### <a name="parameters"></a>參數  
 `value`  
 媒體櫃受管理的命名空間名稱。  
  
## <a name="definition"></a>定義  
 `GUID_ManagedName`則定義於 Cor.h，如下所示：  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>備註  
 自訂介面屬性類型程式庫中定義物件之中繼資料。  
  
 使用<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType>或<xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType>從屬性擷取受管理的名稱。  
  
 如需詳細資訊，請參閱[介面屬性](/cpp/windows/interface-attributes)Visual c + + 參考文件。  
  
## <a name="example"></a>範例  
 下列範例顯示使用程式庫定義`GUID_ManagedName`屬性。  
  
```  
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
 **標頭：** Cor.h
