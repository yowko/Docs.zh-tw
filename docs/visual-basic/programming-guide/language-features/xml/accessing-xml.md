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
ms.openlocfilehash: 8ffe6d5ed368aee6d6984ec6ab28c8832921a3f8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080175"
---
# <a name="accessing-xml-in-visual-basic"></a>在 Visual Basic 中存取 XML

Visual Basic 提供 XML 軸屬性來存取和流覽 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 結構。 這些屬性使用特殊語法，可讓您藉由指定 XML 名稱來存取元素和屬性。  
  
 下表列出的語言功能，可讓您存取 Visual Basic 中的 XML 元素和屬性。  
  
### <a name="xml-axis-properties"></a>XML 軸屬性  
  
|屬性描述|範例|描述|  
|--------------------------|-------------|-----------------|  
|*子軸*|`contact.<phone>`|取得專案的子專案的所有 `phone` 元素 `contact` 。|  
|*attribute 軸*|`phone.@type`|取得 `type` 元素的所有屬性 `phone` 。|  
|*下階座標軸*|`contacts...<name>`|取得專案 `name` 的所有專案 `contacts` ，不論階層中的深度如何進行。|  
|*擴充索引子*|`contacts...<name>(0)`|取得序列中的第一個 `name` 元素。|  
|*value*|`contacts...<name>.Value`|取得序列中第一個物件的字串表示， `Nothing` 如果序列是空的，則為。|  
  
## <a name="in-this-section"></a>本節內容  

 [如何：存取 XML 子系項目](how-to-access-xml-descendant-elements.md)  
 示範如何使用子代軸屬性來存取所有具有指定之名稱的 XML 專案，以及包含在指定之 XML 元素底下的專案。  
  
 [如何：存取 XML 子項目](how-to-access-xml-child-elements.md)  
 示範如何使用子軸屬性來存取 XML 專案中具有指定名稱的所有 XML 子項目。  
  
 [如何：存取 XML 屬性](how-to-access-xml-attributes.md)  
 示範如何使用屬性軸屬性來存取 XML 元素中具有指定名稱的所有 XML 屬性。  
  
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
 提供有關在 Visual Basic 中載入和修改 XML 之章節的連結。  
  
 [XML](index.md)  
 提供描述如何 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 在 Visual Basic 中使用之章節的連結。
