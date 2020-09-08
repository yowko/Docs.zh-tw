---
title: 載入或剖析 XML 時保留空白字元 LINQ to XML
description: 您可以控制填入 XML 樹狀的 LINQ to XML 方法的空白字元行為。 例如，您可以移除記憶體中處理的縮排，或保持原狀。
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: 783a1198f0b1754c690f04159860056a0fbadeb4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552164"
---
# <a name="preserve-white-space-while-loading-or-parsing-xml-linq-to-xml"></a>載入或剖析 XML (LINQ to XML) 時保留空白字元

本文說明如何控制 LINQ to XML 的空白字元行為。

常見的案例是讀取縮排的 XML、建立記憶體中的 XML 樹狀結構，而不含任何空白字元文位元組點 (也就是不保留空白字元) 、對 XML 進行某些作業，然後以縮排儲存 XML。 當您序列化具有格式的 XML 時，只會保留 XML 樹狀結構中的有效空白字元。 這是 LINQ to XML 的預設行為。

其他常見案例為讀取與修改已經過刻意縮排的 XML。 您可能不想用任何方式變更這個縮排。 若要在 LINQ to XML 中這麼做，您可以在載入或剖析 XML 時保留空白字元，並且在序列化 XML 時停用格式設定。

本文描述填入 XML 樹狀結構之方法的空白字元行為。 如需在序列化 XML 樹狀結構時控制空白字元的詳細資訊，請參閱在序列化 [時保留空白字元](preserve-white-space-serializing.md)。

## <a name="behavior-of-methods-that-populate-xml-trees"></a>填入 XML 樹狀結構之方法的行為

下列 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 類別中的方法會填入 XML 樹狀結構。 您可以從檔案、<xref:System.IO.TextReader>、<xref:System.Xml.XmlReader> 或字串填入 XML 樹狀：

- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>

如果方法未採用做 <xref:System.Xml.Linq.LoadOptions> 為引數，此方法將不會保留無意義的空白字元。

在大部分的情況下，如果此方法採用 <xref:System.Xml.Linq.LoadOptions> 當做引數，您可以選擇性地保留有效空白字元當做 XML 樹狀結構中的文字節點。 不過，如果此方法是從 <xref:System.Xml.XmlReader> 載入 XML，<xref:System.Xml.XmlReader> 會決定是否要保留空白字元。 設定 <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> 不會有任何作用。

利用這些方法，如果保留空白字元，會將有效的空白字元插入到 XML 樹狀結構中，當做 <xref:System.Xml.Linq.XText> 節點。 如果不保留空白字元，則不會插入文位元組點。

您可以使用 <xref:System.Xml.XmlWriter> 來建立 XML 樹狀結構。 寫入到 <xref:System.Xml.XmlWriter> 中的節點會填入樹狀結構中。 不過，當您使用這個方法建置 XML 樹狀時，不管節點是否為空白字元，也不管空白字元是否有效，都會保留所有節點。
