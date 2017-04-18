---
title: "序列化程序中的步驟 | Microsoft Docs"
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
  - "二進位序列化, 步驟"
  - "序列化, 步驟"
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 序列化程序中的步驟
在[格式子](frlrfSystemRuntimeSerializationFormatterClassTopic)上呼叫 [Serialize](frlrfSystemRuntimeSerializationFormatterClassSerializeTopic) 方法時，物件序列化會按照下列規則順序繼續進行：  
  
-   進行檢查以判斷格式子是否有代理選取器。若格式子有代理選取器，檢查代理選取器是否處理指定型別的物件。若選取器可處理物件型別，會對代理選取器呼叫 **ISerializable.GetObjectData**。  
  
-   若無代理選取器，或它不處理物件型別，則檢查以判斷物件是否以 [Serializable](frlrfSystemSerializableAttributeClassTopic) 屬性標記。若物件未以該屬性標記，會擲回 [SerializationException](frlrfSystemRuntimeSerializationSerializationExceptionClassTopic)。  
  
-   若物件有適當地標記，檢查物件是否實作 [ISerializable](frlrfSystemRuntimeSerializationISerializableClassTopic) 介面。若物件實作，會對物件呼叫 [GetObjectData](frlrfSystemRuntimeSerializationISerializableClassGetObjectDataTopic)。  
  
-   若物件未實作 **ISerializable**，且使用預設序列化原則，則會序列化所有未標記為 [NonSerialized](frlrfSystemNonSerializedAttributeClassTopic) 的欄位。  
  
## 請參閱  
 [二進位序列化](../../../docs/framework/serialization/binary-serialization.md)   
 [Remote Objects](http://msdn.microsoft.com/zh-tw/515686e6-0a8d-42f7-8188-73abede57c58)   
 [XML 和 SOAP 序列化](../../../docs/framework/serialization/xml-and-soap-serialization.md)