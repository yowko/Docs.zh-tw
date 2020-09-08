---
title: 序列化時保留空白字元-LINQ to XML
description: 在序列化 XML 樹狀結構時，您可以使用各種方式來控制空白字元。
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d907e68a2df3905794b555954330f31b5e75655
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552157"
---
# <a name="preserve-white-space-while-serializing-linq-to-xml"></a>將 (LINQ to XML 序列化時保留空白字元) 

本文描述如何在序列化 XML 樹狀結構時控制空白字元。

常見的案例是讀取縮排的 XML、建立記憶體中的 XML 樹狀結構，而不含任何空白字元文位元組點 (也就是不保留空白字元) 、對 XML 進行某些作業，然後以縮排儲存 XML。 當您序列化具有格式的 XML 時，只會保留 XML 樹狀結構中的有效空白字元。 這是 LINQ to XML 的預設行為。

其他常見案例為讀取與修改已經過刻意縮排的 XML。 您可能不想用任何方式變更這個縮排。 若要在 LINQ to XML 中這麼做，您可以在載入或剖析 XML 時保留空白字元，並且在序列化 XML 時停用格式設定。

## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>序列化 XML 樹狀結構之方法的空白字元行為

下列 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 類別中的方法會序列化 XML 樹狀結構。 您可以將 XML 樹狀結構序列化至檔案、<xref:System.IO.TextReader> 或 <xref:System.Xml.XmlReader>。 `ToString` 方法會序列化至字串。

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- [XElement.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
- [XDocument.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)

如果方法未採用做 <xref:System.Xml.Linq.SaveOptions> 為引數，則此方法將會格式化 (縮排) 序列化的 XML。 在此情況下，會宣告 XML 樹狀結構中的所有有效空白字元。

如果此方法採用 <xref:System.Xml.Linq.SaveOptions> 當做引數，您就可以指定該方法不格式化 (縮排) 序列化的 XML。 在此情況下，會保留 XML 樹狀中的所有空白字元。
