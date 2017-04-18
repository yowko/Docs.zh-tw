---
title: "持續性儲存體 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "二進位序列化, 持續性儲存體"
  - "持續性儲存體"
  - "序列化, 持續性儲存體"
ms.assetid: b112c0dd-93e2-4eef-908d-5963f80bab65
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 持續性儲存體
經常有需要將物件的欄位值儲存至磁碟，稍後再擷取此資料的情況。儘管不需序列化就可以輕易取得，但是此做法經常繁瑣而易出錯，而且當需要追蹤物件階層時會變得越來越複雜。想像撰寫包含數千個物件的大型企業應用程式，且必須對所有物件撰寫程式碼，將欄位和屬性儲存至磁碟和從磁碟中還原。序列化提供方便的機制達到此目的。  
  
 Common Language Runtime 管理物件在記憶體中儲存的方式，並使用[反映](../../../docs/framework/reflection-and-codedom/reflection.md)提供自動的序列化機制。當物件序列化後，類別名稱、組件以及類別執行個體的所有資料成員都會寫入儲存區。物件通常將對其他執行個體的參考儲存在成員變數中。將類別序列化後，序列化引擎會追蹤已序列化的參考物件，確保不會將相同的物件序列化多次。隨 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 所提供的序列化架構會正確地自動處理物件圖形和循環參考。對物件圖形的唯一要求是所有由已序列化物件所參考的物件，必須也標示為[可序列化](frlrfSystemSerializableAttributeClassTopic) \(如需更詳細資訊，請參閱[基本序列化](../../../docs/framework/serialization/basic-serialization.md)\)。若不這麼做，當序列化程式嘗試序列化未標示的物件時，將擲回例外狀況。  
  
 將已序列化的類別還原序列化時，會重新建立該類別且自動還原所有資料成員的值。  
  
## 請參閱  
 [序列化概念](../../../docs/framework/serialization/serialization-concepts.md)   
 [Remote Objects](http://msdn.microsoft.com/zh-tw/515686e6-0a8d-42f7-8188-73abede57c58)   
 [XML 和 SOAP 序列化](../../../docs/framework/serialization/xml-and-soap-serialization.md)