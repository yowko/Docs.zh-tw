---
title: 存取 XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 282b7d91ec7cfe2f587c67bc9a982f0da22ad925
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410305"
---
# <a name="accessing-xml-in-visual-basic"></a>在 Visual Basic 中存取 XML
Visual Basic 提供用於存取和流覽結構的 XML 軸屬性 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 。 這些屬性會使用特殊語法，讓您藉由指定 XML 名稱來存取元素和屬性。  
  
 下表列出的語言功能可讓您存取 Visual Basic 中的 XML 元素和屬性。  
  
### <a name="xml-axis-properties"></a>XML 軸屬性  
  
|屬性描述|範例|描述|  
|--------------------------|-------------|-----------------|  
|*子軸*|`contact.<phone>`|取得專案 `phone` 之子專案的所有元素 `contact` 。|  
|*attribute 軸*|`phone.@type`|取得元素的所有 `type` 屬性 `phone` 。|  
|*下階座標軸*|`contacts...<name>`|取得專案 `name` 的所有專案 `contacts` ，不論其出現在階層中的深度為何。|  
|*延伸模組索引子*|`contacts...<name>(0)`|取得序列中的第一個 `name` 元素。|  
|*值*|`contacts...<name>.Value`|取得序列中第一個物件的字串表示， `Nothing` 如果序列是空的，則為。|  
  
## <a name="in-this-section"></a>本節內容  
 [如何：存取 XML 子系項目](how-to-access-xml-descendant-elements.md)  
 示範如何使用子代軸屬性來存取所有具有指定名稱且包含在指定之 XML 專案底下的 XML 元素。  
  
 [如何：存取 XML 子項目](how-to-access-xml-child-elements.md)  
 示範如何使用子軸屬性來存取 XML 元素中所有具有指定名稱的 XML 子專案。  
  
 [如何：存取 XML 屬性](how-to-access-xml-attributes.md)  
 示範如何使用屬性軸屬性來存取 XML 元素中所有具有指定名稱的 XML 屬性。  
  
 [如何：宣告和使用 XML 命名空間前置字元](how-to-declare-and-use-xml-namespace-prefixes.md)  
 示範如何宣告 XML 命名空間前置詞，並使用它來建立和存取 XML 元素。  
  
## <a name="related-sections"></a>相關章節  
 [XML 軸屬性](../../../language-reference/xml-axis/index.md)  
 提供描述各種 XML 存取屬性之區段的連結。  
  
 [Visual Basic 中的 LINQ to XML 概觀](overview-of-linq-to-xml.md)  
 提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 在 Visual Basic 中使用的簡介。  
  
 [在 Visual Basic 中建立 XML](creating-xml.md)  
 提供在 Visual Basic 中使用 XML 常值的簡介。  
  
 [在 Visual Basic 中管理 XML](manipulating-xml.md)  
 提供有關在 Visual Basic 中載入和修改 XML 的章節連結。  
  
 [XML](index.md)  
 提供章節的連結，說明如何 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 在 Visual Basic 中使用。
