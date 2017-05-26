---
title: "命名空間概觀 (LINQ to XML) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 73eb9d0808666238e55abdf53888ec0f9b501fe2
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="namespaces-overview-linq-to-xml"></a>命名空間概觀 (LINQ to XML)
本主題介紹 <xref:System.Xml.Linq.XName> 類別和 <xref:System.Xml.Linq.XNamespace> 類別的命名空間。  
  
## <a name="xml-names"></a>XML 名稱  
 XML 名稱通常是 XML 程式設計中的複雜性來源。 XML 名稱包含 XML 命名空間 (也稱為 XML 命名空間 URI) 和區域名稱。 XML 命名空間與以 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] 為基礎之程式中的命名空間很相似。 它可讓您唯一限定項目和屬性的名稱。 這有助於防止 XML 文件各個部分間的名稱衝突。 當您宣告 XML 命名空間時，您可以選擇僅在該命名空間中為唯一的區域名稱。  
  
 XML 名稱的另一個層面為 XML「命名空間前置詞」**。 XML 前置詞會造成 XML 名稱大部分的複雜度。 這些前置詞可讓您建立 XML 命名空間的捷徑，讓 XML 文件更精簡而且更容易了解。 不過，XML 前置詞的內容與其意義相依，這會增加複雜度。 例如，XML 前置詞 `aw` 可以與 XML 樹狀結構一部分的其中一個 XML 命名空間產生關聯，並與 XML 樹狀結構不同部分的不同 XML 命名空間產生關聯。  
  
 使用 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 搭配 C# 的其中一項優點是，您不必使用 XML 前置詞。 當 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 載入或剖析 XML 文件時，每個 XML 前置詞都會解析為其對應的 XML 命名空間。 之後，當您處理使用命名空間的文件時，您幾乎永遠都要透過命名空間 URI (而非透過命名空間前置詞) 存取命名空間。 當開發人員在 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 中使用 XML 名稱時，他們一律要使用完整的 XML 名稱 (也就是，XML 命名空間加上區域名稱)。 不過，必要時，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 可讓您使用並控制命名空間前置詞。  
  
 在 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 中，代表 XML 名稱的類別是 <xref:System.Xml.Linq.XName>。 XML 名稱經常出現在整個 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API 中，而且無論哪裡需要 XML 名稱，您都會找到 <xref:System.Xml.Linq.XName> 參數。 但很少會直接使用 <xref:System.Xml.Linq.XName>。 <xref:System.Xml.Linq.XName> 包含字串的隱含轉換。  
  
 如需詳細資訊，請參閱 <xref:System.Xml.Linq.XNamespace> 和 <xref:System.Xml.Linq.XName>。  
  
## <a name="see-also"></a>另請參閱  
 [處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
