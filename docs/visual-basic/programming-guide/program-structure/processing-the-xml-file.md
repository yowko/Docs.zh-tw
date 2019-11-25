---
title: 處理 XML 檔案
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 4230fd88b4b60c631135f5b7fb15f4b6272b5351
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347307"
---
# <a name="processing-the-xml-file-visual-basic"></a>處理 XML 檔案 (Visual Basic)
編譯器會針對程式碼中，標記為要產生文件的每個建構產生識別碼字串。 (For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct. Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item.  
  
 The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.  
  
 編譯器在產生識別碼字串時會遵守下列規則：  
  
- 字串中未放置任何空白字元。  
  
- 識別碼字串的第一個部分會識別所識別的成員種類，格式為單一字元後面接著一個冒號。 The following member types are used.  
  
|字元|描述|  
|---|---|  
|N|namespace<br /><br /> You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.|  
|T|type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|field: `Dim`|  
|P|property: `Property` (including default properties)|  
|M|method: `Sub`, `Function`, `Declare`, `Operator`|  
|E|event: `Event`|  
|!|錯誤字串<br /><br /> 字串的其餘部分提供與錯誤相關的資訊。 The Visual Basic compiler generates error information for links that cannot be resolved.|  
  
- The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace. The name of the item, its enclosing type(s), and the namespace are separated by periods. If the name of the item itself contains periods, they are replaced by the number sign (#). It is assumed that no item has a number sign directly in its name. For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.  
  
- 針對屬性和方法，如果有方法的引數，則後面會接著以括弧括住的引數清單。 如果沒有任何引數，就不會出現括弧。 引數會以逗號分隔。 The encoding of each argument follows directly how it is encoded in a .NET Framework signature.  
  
## <a name="example"></a>範例  
 The following code shows how the ID strings for a class and its members are generated.  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>請參閱

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
