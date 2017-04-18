---
title: "GUID_ManagedName 屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: 
  - "GUID_ManagedName"
apilocation: 
  - "alink.dll"
apitype: "COM"
f1_keywords: 
  - "GUID_ManagedName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GUID_ManagedName 屬性"
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# GUID_ManagedName 屬性
定義一個自訂介面屬性來指定 「 元件物件模型 \(COM\) 程式庫的受管理的命名空間名稱。  
  
## 語法  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
#### 參數  
 `value`  
 程式庫的受管理的命名空間名稱。  
  
## 定義  
 `GUID_ManagedName` 定義在 Cor.h，如下所示︰  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## 備註  
 自訂介面屬性會定義物件之中繼資料型別程式庫中。  
  
 使用 <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=fullName> 或 <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=fullName> 從屬性擷取受管理的名稱。  
  
 如需詳細資訊，請參閱 [Interface Attributes](../Topic/Interface%20Attributes.md) Visual c \+ \+ 參考文件。  
  
## 範例  
 下列範例示範使用程式庫定義 `GUID_ManagedName` 屬性。  
  
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
  
## 需求  
 **標頭：**Cor.h