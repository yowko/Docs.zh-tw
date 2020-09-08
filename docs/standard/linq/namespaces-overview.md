---
title: 命名空間總覽-LINQ to XML
description: 深入瞭解 XML 名稱、XML 命名空間和 XML 命名空間前置詞，以及 XName 和 XNamespace 類別。
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: 81fe678a8d6be32461c675cc527595033e826165
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552180"
---
# <a name="namespaces-overview-linq-to-xml"></a>命名空間總覽 (LINQ to XML) 

本文介紹 *xml 名稱*、 *xml 命名*空間、 *xml 命名空間*前置詞，以及 <xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 類別。

XML 名稱通常是 XML 程式設計中的複雜性來源。 XML 名稱包含 XML 命名空間 (也稱為 XML 命名空間 URI) 和區域名稱。 XML 命名空間類似于 .NET 程式中的命名空間。 它可讓您唯一限定專案和屬性的名稱，以避免 XML 檔各個部分間的名稱衝突。 當您宣告 XML 命名空間時，您可以選取只在該命名空間內必須是唯一的本機名稱。

XML 名稱的另一個層面是 XML 命名空間前置詞，這會導致 XML 名稱的大部分複雜性。 這些前置詞可讓您建立 XML 命名空間的捷徑，讓 XML 文件更精簡而且更容易了解。 不過，XML 前置詞的意義取決於內容，這會增加複雜度。 例如，XML 前置詞 `aw` 可以與 xml 樹狀結構中的一個 xml 命名空間相關聯，並且在另一個元件中使用不同的命名空間。

使用 LINQ to XML 搭配 c # 的其中一項優點是，您不需要使用 XML 前置詞。 當 LINQ to XML 載入或剖析 XML 檔時，會將每個 XML 前置詞解析為其對應的 XML 命名空間。 之後，當您處理使用命名空間的文件時，您幾乎永遠都要透過命名空間 URI (而非透過命名空間前置詞) 存取命名空間。 當開發人員在 LINQ to XML 使用 XML 名稱時，它們一律會使用完整的 XML 名稱， (也就是 XML 命名空間和本機名稱) 。 不過，LINQ to XML 可讓您視需要使用和控制命名空間前置詞。

使用 LINQ to XML 搭配 Visual Basic 和 XML 常值時，您必須在使用命名空間中的檔時使用命名空間前置詞。

在 LINQ to XML 中，代表 XML 名稱的類別是 <xref:System.Xml.Linq.XName> 。 XML 名稱會經常出現在 LINQ to XML API 中，而且每當需要 XML 名稱時，您就會發現一個 <xref:System.Xml.Linq.XName> 參數。 不過，您幾乎不會直接使用 <xref:System.Xml.Linq.XName>。 <xref:System.Xml.Linq.XName> 包含字串的隱含轉換。

如需詳細資訊，請參閱 <xref:System.Xml.Linq.XNamespace> 和 <xref:System.Xml.Linq.XName>。
