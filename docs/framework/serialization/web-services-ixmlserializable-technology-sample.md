---
title: "Web 服務 IXmlSerializable 技術範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Web 服務 IXmlSerializable 技術範例
[下載範例](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 這個範例會示範如何在 ASP.NET Web 服務中使用 <xref:System.Xml.Serialization.IXmlSerializable> 來控制自訂型別的序列化。  
  
### 若要使用 Visual Studio 建置範例  
  
1.  開啟 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]，從 \[**檔案**\] 功能表中選取 \[**新網站**\]。  
  
2.  在 \[**新網站**\] 對話方塊的左窗格中選取想要的程式設計語言，再從右窗格中選取 \[**ASP.NET Web 服務**\]。  
  
3.  輸入 **IXmlSerializable** 做為新 Web 服務的名稱。  
  
4.  在 \[方案總管\] 視窗中，以滑鼠右鍵按一下 Service.asmx 的圖示，然後選取 \[**刪除**\]。另外也請針對 Service.asmx 的 Codebehind 檔案執行這個步驟。  
  
5.  以滑鼠右鍵按一下專案目錄，然後選取 \[**加入現有項目**\]。在對話方塊中，巡覽至語言特定目錄的 Service 子目錄。  
  
6.  選取 Service.asmx，然後對 Service.asmx 的 Codebehind 檔案重複這個步驟。  
  
7.  開啟 [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]，巡覽至包含上述步驟 3 所建立之 IXmlSerializable 目錄的目錄。  
  
8.  以滑鼠右鍵按一下 IXmlSerializable 目錄的圖示，然後選取 \[**共用和安全性**\]。  
  
9. 在 \[Web 共用\] 索引標籤中選取 \[**共用這個資料夾**\]，並確認預設設定值，包括名稱 IXmlSerializable。  
  
10. 按一下 \[**確定**\]。  
  
### 若要執行範例  
  
1.  開啟瀏覽器視窗，並選取網址列。  
  
2.  輸入 **http:\/\/localhost\/IXmlSerializable\/Service.asmx**。  
  
## 請參閱  
 <xref:System.Xml.Serialization.IXmlSerializable>   
 <xref:System.Xml.Serialization>   
 <xref:System.Xml.XmlConvert>   
 <xref:System.Xml.XmlQualifiedName>   
 <xref:System.Xml.XmlReader>   
 <xref:System.Xml.Schema.XmlSchema>   
 <xref:System.Xml.Schema.XmlSchemaSet>   
 <xref:System.Xml.XmlUrlResolver>   
 <xref:System.Xml.XmlWriter>