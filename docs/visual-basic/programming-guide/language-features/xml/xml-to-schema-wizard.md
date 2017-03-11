---
title: "XML to Schema Wizard (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlToSchemaWizard"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML IntelliSense [Visual Basic]"
  - "XML [Visual Basic], IntelliSense"
  - "IntelliSense [Visual Basic], XML"
  - "XML schemas, creating"
ms.assetid: 98c495ba-8f37-4517-a0db-aa738611ab76
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# XML to Schema Wizard (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

XML To Schema 精靈可以用來建立從一個或多個 XML 文件推斷而來的 XML 結構描述集，並將它包含於專案中。  您可以使用任何以文字檔、來自 HTTP 網際網路位址亦或輸入或貼至 \[XML To Schema 精靈\] 之 XML 的形式組合而成的 XML 文件。  
  
 在 Visual Basic 中，XML 結構描述可用來對 XML 屬性提供 IntelliSense。  如需詳細資訊，請參閱 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)和 [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)。  
  
> [!NOTE]
>  在執行 XML To Schema 精靈之前，建議您先移除精靈之前為專案產生的任何現有 XSD 檔案。  如果您推斷的 XML 結構描述集與現有的結構描述集相符，則可能會發生衝突，而且 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 將無法對 XML 屬性提供 IntelliSense。  
  
 XML To Schema 精靈會使用 <xref:System.Xml.Schema.XmlSchemaInference> 類別，為提供的 XML 建立結構描述，  因此可能會為結構描述集建立多個結構描述檔案。  針對提供的 XML 中的各個 XML 命名空間，會分別建立一個可延伸結構描述定義 \(Extensible Schema Definition，XSD\) 檔案。  如需詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法。  
  
 若要存取 \[XML To Schema 精靈\]，請按一下 \[**專案**\] 功能表上的 \[**加入新項目**\]，然後從 \[**資料**\] 或 \[**一般項目**\] 樣板群組加入 \[**XML To Schema**\] 樣板。  當您已包含所有要從中推斷 XML 結構描述集的 XML 文件來源時，請按一下 \[**確定**\] 以建立推斷的結構描述集。  
  
 **來源型別**  
 這個資料行會顯示 XML 文件來源的型別：\[**檔案**\]、\[**URL**\] 或 \[**XML**\]。  
  
 **XML 文件位置**  
 這個資料行會顯示 XML 文件的路徑。  針對輸入或貼上的 XML 文件，會顯示 XML 文件的內容。  
  
 **從檔案加入**  
 使用檔案總管\]中，按一下這個按鈕將XML文件。  
  
 **從 Web 加入**  
 按一下這個按鈕，即可提供 XML 文件的 HTTP 位址。  
  
 **輸入或貼上 XML**  
 按一下這個按鈕，即可將 XML 文件輸入或貼入到對話方塊。  
  
## 請參閱  
 <xref:System.Xml.Schema.XmlSchemaInference>   
 [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)