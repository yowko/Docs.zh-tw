---
title: System.Xml 使用方式
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce9869d538b69af9beaa74be3300175f279b8f53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572810"
---
# <a name="systemxml-usage"></a>System.Xml 使用方式
本節討論中的幾種類型的使用方式的相關<xref:System.Xml?displayProperty=nameWithType>無法用來代表 XML 資料的命名空間。  
  
 **X 不**使用<xref:System.Xml.XmlNode>或<xref:System.Xml.XmlDocument>來表示 XML 資料。 使用的執行個體非<xref:System.Xml.XPath.IXPathNavigable>， <xref:System.Xml.XmlReader>， <xref:System.Xml.XmlWriter>，或是子類型的<xref:System.Xml.Linq.XNode>改為。 `XmlNode` 和`XmlDocument`不專為公開在公用 Api。  
  
 **✓ 不要**使用`XmlReader`， `IXPathNavigable`，或是子類型的`XNode`做為輸入或輸出的接受或傳回 XML 的成員。  
  
 使用這些抽象概念，而不是`XmlDocument`， `XmlNode`，或<xref:System.Xml.XPath.XPathDocument>，因為這可分隔從記憶體中 XML 文件的特定實作的方法，並讓他們使用的虛擬公開 （expose） 的 XML 資料來源`XNode``XmlReader`，或<xref:System.Xml.XPath.XPathNavigator>。  
  
 **X 不**子類別`XmlDocument`如果您想要建立代表基礎物件模型或資料來源的 XML 檢視表的型別。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)
