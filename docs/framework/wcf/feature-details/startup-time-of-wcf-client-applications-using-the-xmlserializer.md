---
title: "HOW TO：使用 XmlSerializer 改善 WCF 用戶端應用程式的啟動時間 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HOW TO：使用 XmlSerializer 改善 WCF 用戶端應用程式的啟動時間
使用資料型別 \(可使用 <xref:System.Xml.Serialization.XmlSerializer> 加以序列化\) 的服務和用戶端應用程式會在執行階段針對這些資料型別產生和編譯序列化程式碼，這可能會導致啟動的效能變慢。  
  
> [!NOTE]
>  預先產生的序列化程式碼只能用於用戶端應用程式中，而不能用於服務中。  
  
 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 可以透過從這些應用程式的已編譯組件產生必要序列化程式碼的方式，改善應用程式的啟動效能。Svcutil.exe 會針對已編譯的應用程式組件中可使用 <xref:System.Xml.Serialization.XmlSerializer> 加以序列化的服務合約所使用的所有資料型別，產生序列化程式碼。使用 <xref:System.Xml.Serialization.XmlSerializer> 的服務和作業合約會標記為 <xref:System.ServiceModel.XmlSerializerFormatAttribute>。  
  
### 若要產生 XmlSerializer 序列化程式碼  
  
1.  將服務或用戶端程式碼編譯至一或多個組件。  
  
2.  開啟 \[SDK 命令提示字元\]。  
  
3.  在命令提示字元中，使用下列格式啟動 Svcutil.exe 工具。  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     `assemblyPath` 引數會指定包含服務合約類型之組件的路徑。Svcutil.exe 會針對已編譯的應用程式組件中可使用 <xref:System.Xml.Serialization.XmlSerializer> 加以序列化的服務合約所使用的所有資料型別，產生序列化程式碼。  
  
     Svcutil.exe 只會產生 C\# 序列化程式碼。每個輸入組件會產生一個原始程式碼檔案。您無法使用 **\/language** 參數來變更所產生程式碼的語言。  
  
     若要指定相依組件的路徑，請使用 **\/reference** 選項。  
  
4.  使用下列其中一個選項，將產生的序列化程式碼提供給應用程式使用：  
  
    1.  將產生的序列化程式碼編譯至名為 \[*original assembly*\].XmlSerializers.dll \(例如，MyApp.XmlSerializers.dll\) 的不同組件。您的應用程式必須能夠載入這個組件，而這個組件必須使用與原始組件相同的金鑰來簽署。如果要重新編譯原始組件，則必須重新產生序列化組件。  
  
    2.  將產生的序列化程式碼編譯至不同的組件，並使用可使用 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 的服務合約上的 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute>。將 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> 或 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> 屬性設定為指向已編譯的序列化組件。  
  
    3.  將產生的序列化程式碼編譯至應用程式組件，並將 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> 加入至可使用 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 的服務合約。請勿設定 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> 或 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> 屬性。預設的序列化組件會假設為目前的組件。  
  
## 範例  
 下列命令會針對組件中任何服務合約所使用的 `XmlSerializer` 型別，產生序列化型別。  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## 請參閱  
 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)