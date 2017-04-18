---
title: "選擇式序列化 | Microsoft Docs"
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
  - "二進位序列化, 選擇式序列化"
  - "序列化, 選擇式序列化"
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 選擇式序列化
類別經常包含不應序列化的欄位。例如，假設類別在成員變數中儲存執行緖 ID。當類別還原序列化時，類別在序列化時儲存 ID 的執行緒可能已不再執行，因此序列化此值就沒有意義。您可如下所示，以 [NonSerialized](frlrfSystemNonSerializedAttributeClassTopic) 屬性標記成員變數，避免成員變數遭序列化。  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```  
  
 如果可能的話，讓可能含有安全性顧慮資料的物件不可序列化。如果物件必須序列化，請套用 **NonSerialized** 屬性至儲存敏感資料的特定欄位。若您未將這些欄位排除在序列化範圍外，請留意它們所儲存的資料可能公開給擁有序列化權限的所有程式碼。如需有關撰寫安全序列化程式碼的詳細資訊，請參閱[安全性和序列化](../../../docs/framework/misc/security-and-serialization.md)。  
  
## 請參閱  
 [二進位序列化](../../../docs/framework/serialization/binary-serialization.md)   
 [Remote Objects](http://msdn.microsoft.com/zh-tw/515686e6-0a8d-42f7-8188-73abede57c58)   
 [XML 和 SOAP 序列化](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md)