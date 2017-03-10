---
title: "如何：使用字典儲存事件執行個體 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "事件 [C#], 在字典中儲存執行個體"
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# 如何：使用字典儲存事件執行個體 (C# 程式設計手冊)
`accessor-declarations` 的用法之一是公開大量的事件但不配置每個事件的欄位，而是改用字典來儲存事件執行個體。  不過，這只在您擁有大量的事件，但預期大多數事件都不會實作的情況下才有用。  
  
## 範例  
 [!code-cs[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/csharp/how-to-use-a-dictionary-_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [事件](../../../csharp/programming-guide/events/index.md)   
 [委派](../../../csharp/programming-guide/delegates/index.md)