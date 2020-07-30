---
title: 序列化至 File、TextWriter 和 XmlWriter
description: '瞭解在 c # 中使用 ToString 或 Save 方法將 XML 樹狀結構序列化為檔案、無效或 XmlWriter 的選項。'
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 43c51ae7e9bf1a7848d45fd900424d6186671e53
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302382"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>序列化至 File、TextWriter 和 XmlWriter

您可以將 XML 樹狀序列化至 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。

您可以使用 <xref:System.Xml.Linq.XDocument> 方法，將任何 XML 元件 (包括 <xref:System.Xml.Linq.XElement> 和 `ToString`) 序列化至字串。

如果您要在序列化至字串時隱藏格式，您可以使用 <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> 方法。

序列化至檔案時的預設行為是格式化 (縮排) 所產生的 XML 文件。 當您縮排時，不會保留 XML 樹狀中的無效空白字元。 若要使用格式序列化，請使用下列沒有採用 <xref:System.Xml.Linq.SaveOptions> 當做引數之方法的其中一個多載：

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

如果您想要選擇不縮排和不保留 XML 樹狀結構中的無效空白字元，請使用下列採用 <xref:System.Xml.Linq.SaveOptions> 當做引數之方法的其中一個多載：

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

如需範例，請參閱適當的參考主題。

## <a name="see-also"></a>另請參閱

- [序列化 XML 樹狀結構 (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
