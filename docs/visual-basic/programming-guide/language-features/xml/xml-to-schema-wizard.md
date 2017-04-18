---
title: "XML to Schema 精靈 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlToSchemaWizard
dev_langs:
- VB
helpviewer_keywords:
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
- XML schemas, creating
ms.assetid: 98c495ba-8f37-4517-a0db-aa738611ab76
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d0c9c0247f3d9934ef973c7322cb098f9b445a5a
ms.lasthandoff: 03/13/2017

---
# <a name="xml-to-schema-wizard-visual-basic"></a>XML to Schema 精靈 (Visual Basic)
使用 XML 結構描述精靈以建立從一個或多個 XML 文件推斷 XML 結構描述集，並將它包含您的專案。 您可以使用文字檔、 XML 從 HTTP 網際網路位址或輸入或貼到 XML to Schema 精靈的 XML 格式的 XML 文任何的件組合。  
  
 XML 結構描述可在 Visual Basic 中的 XML 屬性來提供 IntelliSense。 如需詳細資訊，請參閱[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)和[Visual Basic 中的 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)。  
  
> [!NOTE]
>  在執行 XML 結構描述精靈 之前，建議您從先前由精靈所產生的專案中移除任何現有的 XSD 檔案。 如果推斷 XML 結構描述集符合現有的結構描述集時，可能會發生衝突和[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]不能為 XML 屬性提供 IntelliSense。  
  
 XML to Schema 精靈使用<xref:System.Xml.Schema.XmlSchemaInference>類別來建立提供 XML 結構描述。</xref:System.Xml.Schema.XmlSchemaInference> 如此一來，多個結構描述檔案可能會建立結構描述集。 每個 XML 命名空間中提供的 XML，會建立可延伸結構描述定義 (XSD) 檔案。 如需詳細資訊，請參閱<xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A>方法。</xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A>  
  
 若要存取 XML to Schema 精靈，請按一下 **加入新項目**上**專案**功能表，並新增**XML 結構描述**範本從**資料**或**一般項目**範本群組。 在包含推斷 XML 結構描述集，從所有 XML 文件來源之後，請按一下**確定**建立推斷的結構描述集。  
  
 **來源類型**  
 此資料行會顯示 XML 文件來源的類型︰**檔案**， **URL**，或**XML**。  
  
 **XML 文件位置**  
 此資料行會顯示 XML 文件的路徑。 輸入或貼上 XML 文件，會顯示 XML 文件的內容。  
  
 **從檔案新增**  
 按一下此按鈕即可使用 [檔案總管] 中加入 XML 文件檔案。  
  
 **將 Web**  
 按一下此按鈕，以提供 XML 文件的 HTTP 位址。  
  
 **輸入或貼上 XML**  
 按一下此按鈕，輸入或貼上 對話方塊中的 XML 文件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Schema.XmlSchemaInference></xref:System.Xml.Schema.XmlSchemaInference>   
 [在 Visual Basic 中的 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)
