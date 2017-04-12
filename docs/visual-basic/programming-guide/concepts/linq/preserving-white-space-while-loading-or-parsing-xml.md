---
title: "載入或剖析 XML2 時保留空白字元 |Microsoft 文件"
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
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
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
ms.openlocfilehash: 39e4270acc0e9a9df5c3855f8c087f41d9612197
ms.lasthandoff: 03/13/2017

---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>載入或剖析 XML 時保留空白字元
這個主題描述如何控制 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 的空白字元行為。  
  
 常見的案例為讀取縮排的 XML、建立沒有任何空白字元文字節點 (也就是不保留空白字元) 的記憶體中 XML 樹狀結構、在 XML 上執行某些作業，然後儲存包含縮排的 XML。 當您序列化具有格式的 XML 時，只會保留 XML 樹狀結構中的有效空白字元。 這是 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 的預設行為。  
  
 其他常見案例為讀取與修改已經過刻意縮排的 XML。 您可能不想用任何方式變更這個縮排。 在 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 中，如果您在載入或剖析 XML 時保留空白字元，並在序列化 XML 時停用格式化，就可以達到這個效果。  
  
 這個主題描述填入 XML 樹狀之方法的空白字元行為。 序列化 XML 樹狀結構時控制空白字元的相關資訊，請參閱[保留泛空白字元時序列化](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)。  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>填入 XML 樹狀之方法的行為  
 下列方法<xref:System.Xml.Linq.XElement>和<xref:System.Xml.Linq.XDocument>類別會填入 XML 樹狀結構。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> 您可以填入 XML 樹狀結構從檔案、 <xref:System.IO.TextReader>、 <xref:System.Xml.XmlReader>，或字串︰</xref:System.Xml.XmlReader> </xref:System.IO.TextReader>  
  
-   <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>  
  
 如果此方法不採用<xref:System.Xml.Linq.LoadOptions>做為引數，此方法將不會保留不顯著泛空白字元。</xref:System.Xml.Linq.LoadOptions>  
  
 在大部分情況下，如果此方法採用<xref:System.Xml.Linq.LoadOptions>做為引數，您可以選擇性地保留有效空白字元當做 XML 樹狀結構中的文字節點。</xref:System.Xml.Linq.LoadOptions> 不過，如果此方法來從 XML 載入<xref:System.Xml.XmlReader>，然後在<xref:System.Xml.XmlReader>決定是否將會保留泛空白字元。</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader> 設定<xref:System.Xml.Linq.LoadOptions>會有任何作用。</xref:System.Xml.Linq.LoadOptions>  
  
 利用這些方法，會保留泛空白字元，如果不顯著泛空白字元插入到 XML 樹狀結構當做<xref:System.Xml.Linq.XText>節點。</xref:System.Xml.Linq.XText> 如果不保留空白字元，則不會插入文字節點。  
  
 您可以使用<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter>建立 XML 樹狀結構 節點寫入<xref:System.Xml.XmlWriter>樹狀目錄中會填入。</xref:System.Xml.XmlWriter> 不過，當您使用這個方法建置 XML 樹狀時，不管節點是否為空白字元，也不管空白字元是否有效，都會保留所有節點。  
  
## <a name="see-also"></a>另請參閱  
 [剖析 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
