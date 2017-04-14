---
title: "基本序列化技術範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 基本序列化技術範例
[下載範例](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 這個範例會說明 Common Language Runtime 將記憶體中的物件 Graph 序列化為資料流的能力。這個範例可以使用 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 或 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 進行序列化。一個內含資料的連結串列 \(Linked List\)，會序列化為檔案資料流或從檔案資料流還原序列化。在這兩種情形下，清單都會顯示供您查看結果。連結串列的型別為 `LinkedList`，是這個範例所定義的型別。  
  
 如需序列化的詳細資訊，請檢視原始程式碼和 build.proj 檔案中的註解。  
  
### 若要使用命令提示字元建置範例  
  
1.  使用 \[命令提示字元\]，巡覽至 Technologies\\Serialization\\Runtime Serialization\\Basic 目錄下的其中一個語言特定子目錄。  
  
2.  根據您選擇的程式設計語言，在命令列輸入 **msbuild SerializationCS.sln**、**msbuild SerializationJSL.sln** 或 **msbuild SerializationVB.sln**。  
  
### 若要使用 Visual Studio 建置範例  
  
1.  開啟 [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]，並巡覽至此範例的任一程式設計語言的子目錄。  
  
2.  根據您選擇的程式設計語言，按兩下 SerializationCS.sln、SerializationJSL.sln 或 SerializationVB.sln 檔案的圖示，在 Visual Studio 中開啟這個檔案。  
  
3.  在 \[**建置**\] 功能表中，選取 \[**建置方案**\]。  
  
 這個範例應用程式將建置於預設的 \\bin 或 \\bin\\Debug 子目錄中。  
  
### 若要執行範例  
  
1.  巡覽至包含已建置之可執行檔的目錄。  
  
2.  在命令列輸入 **Serialization.exe** 以及您想要的參數值。  
  
    > [!NOTE]
    >  這個範例會建置一個主控台應用程式。您必須使用命令提示字元啟動，才能檢視它的輸出。  
  
## 備註  
 這個範例應用程式接受會指出您想執行哪一項測試的命令列參數。若想使用 SOAP 格式子 \(Formatter\)，將包含 10 個節點的清單序列化成名為 **Test.xml** 的檔案，請使用 **sx Test.xml 10** 參數。  
  
 例如：  
  
 **Serialize.exe \-sx Test.xml 10**  
  
 如果想還原序列化前一個範例的 **Test.xml** 檔，請使用 **dx Test.xml** 參數。  
  
 例如：  
  
 **Serialize.exe \-dx Test.xml**  
  
 在上述兩個範例中，命令列參數中的 "x" 表示您想執行 XML SOAP 序列化。如果在相同的位置上使用 "b"，就表示要使用二進位序列化。如果您想嘗試序列化大量的節點，可以將主控台輸出重新導向至檔案中。  
  
 例如：  
  
 **Serialize.exe \-sb Test.bin 10000 \>somefile.txt**  
  
 下面幾點簡短說明了此範例所使用的類別和技術。  
  
-   執行階段序列化  
  
    -   <xref:System.Runtime.Serialization.IFormatter> 用來參考 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 或 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 物件。  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 用來將連結串列序列化成二進位格式的資料流。二進位格式子使用的格式只有 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 型別才了解。不過，資料相當簡明。  
  
    -   <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 用來將連結串列序列化成 SOAP 格式的資料流。SOAP 是一種標準格式。  
  
-   資料流 I\/O  
  
    -   <xref:System.IO.Stream> 用來執行序列化及還原序列化。這個範例所用的特定資料流型別是 <xref:System.IO.FileStream> 型別。不過，序列化可以使用衍生自 <xref:System.IO.Stream> 的任何型別。  
  
    -   <xref:System.IO.File> 用來建立 <xref:System.IO.FileStream> 物件，以便在磁碟上讀取及建立檔案。  
  
    -   <xref:System.IO.FileStream> 用來將連結串列序列化及還原序列化。  
  
## 請參閱  
 [BinaryFormatter 類別](frlrfSystemRuntimeSerializationFormattersBinaryBinaryFormatterClassTopic)   
 [File 類別](frlrfSystemIOFileClassTopic)   
 [FileStream 類別](frlrfSystemIOFileStreamClassTopic)   
 [IFormatter 介面](frlrfSystemRuntimeSerializationIFormatterClassTopic)   
 [Random 類別](https://msdn.microsoft.com/en-us/library/system.random.aspx)   
 [SerializableAttribute 屬性](frlrfSystemSerializableAttributeClassTopic)   
 [SoapFormatter 類別](frlrfSystemRuntimeSerializationFormattersSoapSoapFormatterClassTopic)   
 [Stream 類別](frlrfSystemIOStreamClassTopic)   
 [System.IO 命名空間](https://msdn.microsoft.com/en-us/library/system.io.aspx)   
 [System.Runtime.Serialization 命名空間](frlrfSystemRuntimeSerialization)   
 [System.Xml.Serialization 命名空間](frlrfSystemXmlSerialization)   
 [基本序列化](../../../docs/framework/serialization/basic-serialization.md)   
 [二進位序列化](../../../docs/framework/serialization/binary-serialization.md)   
 [使用屬性控制 XML 序列化](../../../docs/framework/serialization/controlling-xml-serialization-using-attributes.md)   
 [XML 序列化簡介](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [序列化](../../../docs/framework/serialization/index.md)   
 [SOAP Service](http://msdn.microsoft.com/zh-tw/2051c992-28d1-499e-961f-17e9b675cec9)   
 [XML 和 SOAP 序列化](../../../docs/framework/serialization/xml-and-soap-serialization.md)