---
title: "HOW TO：序列化物件 | Microsoft Docs"
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
  - "物件, 序列化步驟"
  - "序列化物件"
ms.assetid: a1207d05-32b2-4953-8582-959607991227
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# HOW TO：序列化物件
若要序列化物件，首先建立要序列化的物件，並設定其公用屬性與欄位。若要執行這項作業，您必須判斷 XML 資料流儲存 \(無論是資料流或檔案\) 的傳輸格式。例如，若 XML 資料流必須以永久形式儲存，請建立 [FileStream](frlrfSystemIOFileStreamClassTopic) 物件。  
  
> [!NOTE]
>  如需更多 XML 序列化的範例，請參閱 [XML 序列化的範例](../../../docs/framework/serialization/examples-of-xml-serialization.md)。  
  
### 序列化物件  
  
1.  建立物件並設定其公用欄位與屬性。  
  
2.  使用物件的型別，建構 <xref:System.Xml.Serialization.XmlSerializer>。如需詳細資訊，請參閱 <xref:System.Xml.Serialization.XmlSerializer> 類別建構函式。  
  
3.  呼叫 <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> 方法，產生 XML 資料流或物件之公用屬性與欄位的檔案表示方式。下列範例將建立檔案。  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new   
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## 請參閱  
 [XML 序列化簡介](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [HOW TO：還原序列化物件](../../../docs/framework/serialization/how-to-deserialize-an-object.md)