---
title: "HOW TO：還原序列化物件 | Microsoft Docs"
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
  - "還原序列化物件"
  - "物件, 還原序列化步驟"
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# HOW TO：還原序列化物件
當您還原序列化物件時，傳輸格式決定您會建立資料流或檔案物件。決定傳輸格式後，您可視需要呼叫 <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> 或 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> 方法。  
  
### 還原序列化物件  
  
1.  使用要還原序列化的物件型別，建構 <xref:System.Xml.Serialization.XmlSerializer>。  
  
2.  呼叫 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> 方法以產生物件的複本。在還原序列化時，您必須將傳回之物件轉換為原始的型別，如下面的範例所示，將物件還原序列化為檔案 \(不過它也能還原序列化成資料流\)。  
  
    ```vb  
    Dim myObject As MySerializableClass  
    ' Construct an instance of the XmlSerializer with the type  
    ' of object that is being deserialized.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To read the file, create a FileStream.  
    Dim myFileStream As FileStream = _  
    New FileStream("myFileName.xml", FileMode.Open)  
    ' Call the Deserialize method and cast to the object type.  
    myObject = CType( _  
    mySerializer.Deserialize(myFileStream), MySerializableClass)  
  
    ```  
  
    ```csharp  
    MySerializableClass myObject;  
    // Construct an instance of the XmlSerializer with the type  
    // of object that is being deserialized.  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(MySerializableClass));  
    // To read the file, create a FileStream.  
    FileStream myFileStream =   
    new FileStream("myFileName.xml", FileMode.Open);  
    // Call the Deserialize method and cast to the object type.  
    myObject = (MySerializableClass)   
    mySerializer.Deserialize(myFileStream)  
    ```  
  
## 請參閱  
 [XML 序列化簡介](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [HOW TO：序列化物件](../../../docs/framework/serialization/how-to-serialize-an-object.md)