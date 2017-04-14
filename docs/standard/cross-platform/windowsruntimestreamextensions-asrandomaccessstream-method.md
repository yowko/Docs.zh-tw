---
title: "WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream"
apilocation: 
  - "System.Runtime.WindowsRuntime.dll"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) 方法
\[在 .NET Framework 4.5.1 \(含\) 以後版本中支援\]  
  
 將指定的資料流轉換為隨機存取資料流。  
  
 **命名空間︰** <xref:System.IO?displayProperty=fullName>   
 **組件：**System.Runtime.WindowsRuntime \(在 System.Runtime.WindowsRuntime.dll 中\)  
  
## 語法  
  
```csharp  
[CLSCompliantAttribute(false)] public static  IRandomAccessStream AsRandomAccessStream(Stream stream)   
```  
  
```vb  
'Declaration <ExtensionAttribute> _ <CLSCompliantAttribute(False)> _ Public Shared Function AsRandomAccessStream ( _         stream As Stream) As IRandomAccessStream   
```  
  
#### 參數  
 `stream`  
  
 類型：<xref:System.IO.Stream?displayProperty=fullName>   
 要轉換的資料流。  
  
## 傳回值  
 類型：[Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)   
 [!INCLUDE[wrt](../../../includes/wrt-md.md)]隨機存取資料流，表示已轉換的資料流。  
  
## 例外狀況  
  
|例外狀況|條件|  
|----------|--------|  
|<xref:System.NotSupportedException>|要轉換的資料流不支援搜尋功能。|  
  
## 備註  
 只有在您開發 Windows 市集應用程式時，這個擴充方法才可供使用。  這個方法會提供方便處理 Windows 市集應用程式中資料流的方式。  您想要轉換的 .NET Framework 資料流必須支援搜尋。  如需詳細資訊，請參閱 <xref:System.IO.Stream.Seek%2A?displayProperty=fullName> 方法。  
  
> [!IMPORTANT]
>  .NET Framework 4.5.1 \(含\) 以後版本可支援這個 API，但 4.5 版不支援。  
  
## 版本資訊  
 **適用於 Windows 市集應用程式的 .NET**  
  
 支援：Windows 8.1  
  
## 請參閱  
 <xref:System.IO.WindowsRuntimeStreamExtensions>   
 [如何：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)