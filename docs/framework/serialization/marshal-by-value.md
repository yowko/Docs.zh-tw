---
title: "以傳值方式封送處理 | Microsoft Docs"
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
  - "二進位序列化, 以傳值方式封送處理"
  - "以傳值方式封送處理的物件"
  - "序列化, 以傳值方式封送處理"
ms.assetid: ee91e8f0-92e0-4732-8015-d17dee154be1
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 以傳值方式封送處理
物件只有在建立它們的應用程式定義域中才有效。除非物件衍生自 [MarshalByRefObject](frlrfSystemMarshalByRefObjectClassTopic) 或是標示為[可序列化](frlrfSystemSerializableAttributeClassTopic)，否則任何嘗試將物件當作參數傳遞，或將物件當作結果傳回的做法都將失敗。若物件標示為**可序列化**，將自動序列化該物件，從一應用程式定義域傳輸至其他定義域，然後在第二應用程式定義域還原序列化，以產生完全相同的物件複本。此程序一般稱為傳值封送處理。  
  
 當物件衍生自 **MarshalByRefObject**，物件參考會從一應用程式定義域傳遞到另一個定義域，而不是物件本身。您也可將衍生自 **MarshalByRefObject** 的物件標示為**可序列化**。當此物件以遠端使用時，已由代理選取器 \([SurrogateSelector](frlrfSystemRuntimeSerializationSurrogateSelectorClassTopic)\) 預先設定並負責序列化的格式子，控制序列化程序並且取代所有具有 Proxy 且衍生自 [MarshalByRefObject](frlrfSystemMarshalByRefObjectClassTopic) 的物件。如果沒有 [SurrogateSelector](frlrfSystemRuntimeSerializationSurrogateSelectorClassTopic)，序列化架構會遵循在[序列化程序中的步驟](../../../docs/framework/serialization/steps-in-the-serialization-process.md)中說明的標準序列化規則。  
  
## 請參閱  
 [序列化概念](../../../docs/framework/serialization/serialization-concepts.md)   
 [Remote Objects](http://msdn.microsoft.com/zh-tw/515686e6-0a8d-42f7-8188-73abede57c58)   
 [XML 和 SOAP 序列化](../../../docs/framework/serialization/xml-and-soap-serialization.md)