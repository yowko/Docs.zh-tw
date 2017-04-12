---
title: "命名空間概觀 (LINQ to XML) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cec2efd31c96af17ad717abaa8f4359210e99a78
ms.lasthandoff: 03/13/2017

---
# <a name="namespaces-overview-linq-to-xml"></a>命名空間概觀 (LINQ to XML)
本主題說明命名空間的<xref:System.Xml.Linq.XName>類別和<xref:System.Xml.Linq.XNamespace>類別。</xref:System.Xml.Linq.XNamespace> </xref:System.Xml.Linq.XName>  
  
## <a name="xml-names"></a>XML 名稱  
 XML 名稱通常是 XML 程式設計中的複雜性來源。 XML 名稱包含 XML 命名空間 (也稱為 XML 命名空間 URI) 和區域名稱。 XML 命名空間與以 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] 為基礎之程式中的命名空間很相似。 它可讓您唯一限定項目和屬性的名稱。 這有助於防止 XML 文件各個部分間的名稱衝突。 當您宣告 XML 命名空間時，您可以選擇僅在該命名空間中為唯一的區域名稱。  
  
 XML 名稱的另一個層面是 XML*命名空間前置詞*。 XML 前置詞會造成 XML 名稱大部分的複雜度。 這些前置詞可讓您建立 XML 命名空間的捷徑，讓 XML 文件更精簡而且更容易了解。 不過，XML 前置詞的內容與其意義相依，這會增加複雜度。 例如，XML 前置詞 `aw` 可以與 XML 樹狀結構一部分的其中一個 XML 命名空間產生關聯，並與 XML 樹狀結構不同部分的不同 XML 命名空間產生關聯。  
  
 當使用[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]Visual Basic 和 XML 常值，必須使用命名空間前置詞的命名空間中的文件時。  
  
 在[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]，代表 XML 名稱的類別是<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName> XML 名稱會經常出現在整個[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]API，而每當需要 XML 名稱時，您會發現<xref:System.Xml.Linq.XName>參數。</xref:System.Xml.Linq.XName> 不過，您幾乎不會直接與<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XName>包含字串的隱含轉換。</xref:System.Xml.Linq.XName>  
  
 如需詳細資訊，請參閱<xref:System.Xml.Linq.XNamespace>和<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XNamespace>  
  
## <a name="see-also"></a>另請參閱  
 [處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
