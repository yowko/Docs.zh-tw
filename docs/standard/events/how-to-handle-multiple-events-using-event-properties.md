---
title: "如何：使用事件屬性處理多個事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "事件處理 [.NET Framework], 含有多個事件"
  - "事件屬性 [.NET Framework]"
  - "事件 [.NET Framework], 多個"
  - "多個事件 [.NET Framework]"
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：使用事件屬性處理多個事件
為了要使用事件屬性，您會在引發事件的類別中定義事件屬性，然後在處理事件的類別中設定事件屬性的委派。  若要在類別中實作多個事件屬性，該類別內部必須儲存及維護為每個事件所定義的委派。  型的方法是實作以事件索引鍵編製索引的委派集合。  
  
 若要儲存每個事件的委派，您可以使用 <xref:System.ComponentModel.EventHandlerList> 類別，或實作您自己的集合。  集合類別必須提供方法，根據事件索引鍵來設定、存取和擷取事件處理常式委派。  例如，您可以使用 <xref:System.Collections.Hashtable> 類別，或是從 <xref:System.Collections.DictionaryBase> 類別衍生自訂類別。  委派集合的實作詳細資料不需要公開至類別之外。  
  
 類別內的每個事件屬性，都會定義一個 add 存取子方法和一個 remove 存取子方法。  事件屬性的 add 存取子會在委派集合中加入輸入委派執行個體。  事件屬性的 remove 存取子會從委派集合中移除輸入委派執行個體。   事件屬性存取子會使用事件屬性的預先定義索引鍵，從委派集合新增和移除執行個體。  
  
### 使用事件屬性處理多個事件  
  
1.  定義在類別中引發事件的委派集合。  
  
2.  定義每個事件的索引鍵。  
  
3.  在引發事件的類別中定義事件屬性。  
  
4.  使用委派集合實作事件屬性的 add 和 remove 存取子方法。  
  
5.  使用公用事件屬性，在處理事件的類別中新增和移除事件處理常式委派。  
  
## 範例  
 下列 C\# 範例會使用 <xref:System.ComponentModel.EventHandlerList> 實作事件屬性 `MouseDown` 及 `MouseUp`，以儲存每個事件的委派。  事件屬性建構的關鍵字會以粗體顯示。  
  
> [!NOTE]
>  [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] 不支援事件屬性。  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## 請參閱  
 <xref:System.ComponentModel.EventHandlerList?displayProperty=fullName>   
 [事件](../../../docs/standard/events/index.md)   
 [System.Web.UI.Control.Events](frlrfSystemWebUIControlClassEventsTopic)   
 [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)