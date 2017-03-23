---
title: "Some subkeys cannot be deleted | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 14562137-af43-4972-84c1-a380a90f7d6c
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Some subkeys cannot be deleted
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

已嘗試刪除登錄機碼，但因無法刪除某些子機碼而導致作業失敗。  這通常是因為缺少使用權限所造成。  
  
### 若要更正這個錯誤  
  
-   確定您有足夠的使用權限能夠刪除指定的子機碼。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy?displayProperty=fullName>   
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:System.Security.Permissions.RegistryPermission>